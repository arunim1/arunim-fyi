---
id: note_01kq5x3w9jekav5f2jaeh71j5q
public: true
---

It sucks to post your Substack post's links on x.com. Your posts might get de-boosted, but even worse, for those of us who only get 2 likes anyways, the link preview looks bad! Substack applies a "focus-crop" and a weird watermark.

Here's a fix. The Cloudflare Worker below sits on a domain you control and serves clean Twitter Card / OG previews for any Substack newsletter you whitelist. Crawlers (i.e. the x.com link unfurler) read the meta tags while humans get redirected to the post.

This particular implementation uses a top-left crop of Substack's OG image (via images.weserv.nl), but you can swap the `transformImage` function if you want a different crop or proxy.

Note: you might do slightly better to store + serve the cropped images in a CMS that you host but i think this works.

To deploy:

1. Pick a domain you own (preferably a high-ranking one) and have on Cloudflare with the orange-cloud proxy enabled. The Worker only runs on proxied traffic, so an unproxied (DNS-only, grey-cloud) record won't work.
2. Edit `NEWSLETTERS` below to map short keys to your Substack newsletter URLs.
3. In the Cloudflare dashboard, go to Workers & Pages → Create → paste the code → Deploy.
4. Add a route on your zone: `yourdomain.com/share/*` → this Worker.
5. Post links shaped like `https://yourdomain.com/share/<key>/<slug>` on x.com instead of the raw Substack URL. Hit the share URL in a browser before posting I think that should warm the edge cache so x.com's unfurler doesn't have to wait ages.

```javascript
// Cloudflare Worker: serves clean Twitter Card / OG previews for Substack newsletters.
//
// Requires: a Cloudflare-proxied (orange-cloud) domain with a Worker route on
// `<yourdomain>/share/*`.
//
// URL shape:
//   https://<yourdomain>/share/<newsletter-key>/<slug>
//   e.g. https://example.com/share/aisn/aisn-71
//
// Behavior:
//   - Known <newsletter-key> + known <slug> (verified by fetching from Substack):
//       * Crawlers get static HTML with OG/Twitter meta tags.
//       * Humans get redirected to the Substack post.
//   - Known <newsletter-key> + unknown/broken <slug>:
//       * Fall back to the newsletter homepage (not a 404).
//   - Unknown <newsletter-key> or malformed path:
//       * 404. Prevents abuse as an open redirector.

const NEWSLETTERS = {
  // key: "https://your-newsletter.substack.com" (or custom Substack domain)
};

// ---------------------------------------------------------------------------

function transformImage(src) {
  if (!src) return "";
  // Deterministic top-left crop of Substack's OG image to 1200x630.
  // weserv scales the source to "cover" the box and anchors at top-left,
  // discarding overflow from the right and/or bottom.
  const u = new URL("https://images.weserv.nl/");
  u.searchParams.set("url", src);
  u.searchParams.set("w", "1200");
  u.searchParams.set("h", "630");
  u.searchParams.set("fit", "cover");
  u.searchParams.set("a", "top-left");
  return u.toString();
}

function pick(html, prop) {
  const patterns = [
    new RegExp(`<meta\\s+[^>]*?(?:property|name)=["']${prop}["'][^>]*?content=["']([^"']+)["']`, "i"),
    new RegExp(`<meta\\s+[^>]*?content=["']([^"']+)["'][^>]*?(?:property|name)=["']${prop}["']`, "i"),
  ];
  for (const re of patterns) {
    const m = html.match(re);
    if (m) return decodeHtmlEntities(m[1]);
  }
  return "";
}

function decodeHtmlEntities(s) {
  return s
    .replace(/&amp;/g, "&")
    .replace(/&lt;/g, "<")
    .replace(/&gt;/g, ">")
    .replace(/&quot;/g, '"')
    .replace(/&#39;/g, "'")
    .replace(/&apos;/g, "'");
}

function esc(s) {
  return String(s || "").replace(/[&<>"']/g, c => ({
    "&": "&amp;", "<": "&lt;", ">": "&gt;", '"': "&quot;", "'": "&#39;"
  }[c]));
}

function notFound() {
  return new Response("Not found", {
    status: 404,
    headers: { "x-robots-tag": "noindex, nofollow" },
  });
}

// ---------------------------------------------------------------------------

export default {
  async fetch(request, env, ctx) {
    const url = new URL(request.url);

    // Expect exactly /share/<newsletter>/<slug>.
    const m = url.pathname.match(/^\/share\/([a-z0-9-]{1,32})\/([a-z0-9][a-z0-9-]{0,200})\/?$/i);
    if (!m) return notFound();

    const key = m[1].toLowerCase();
    const slug = m[2].toLowerCase();

    // Whitelisted newsletter? Closes the open-redirect risk.
    const newsletterBase = NEWSLETTERS[key];
    if (!newsletterBase) return notFound();

    const substackUrl = `${newsletterBase}/p/${slug}`;
    const target = `${substackUrl}?utm_source=x&utm_medium=social&utm_campaign=${slug}`;
    const homepageTarget = `${newsletterBase}/?utm_source=x&utm_medium=social&utm_campaign=${key}`;

    // Edge cache. Key on full URL — the HTML we serve is the same for bots
    // and humans (humans get meta-refresh + JS; bots ignore both), so one
    // cache entry is safe for all user agents.
    const cache = caches.default;
    const cacheKey = new Request(url.toString(), { method: "GET" });
    const hit = await cache.match(cacheKey);
    if (hit) return hit;

    // Fetch Substack and verify the post actually exists. A non-OK response
    // means the slug is wrong or Substack is having a moment — in either
    // case, degrade to sending people to the newsletter homepage rather
    // than a broken post page.
    let title = "", description = "", srcImage = "";
    let postExists = false;
    try {
      const r = await fetch(substackUrl, {
        cf: { cacheTtl: 300 },
        redirect: "follow",
      });
      if (r.ok) {
        postExists = true;
        const html = await r.text();
        title = pick(html, "og:title") || pick(html, "twitter:title") || "";
        description = pick(html, "og:description") || pick(html, "twitter:description") || "";
        srcImage = pick(html, "og:image") || "";
      }
    } catch {}

    // Fallback: post not found → redirect humans to the newsletter homepage,
    // and serve generic homepage OG tags to crawlers.
    const effectiveTarget = postExists ? target : homepageTarget;
    if (!postExists) {
      title = title || "Newsletter";
      description = description || "";
      srcImage = srcImage || "";
    }

    const image = transformImage(srcImage);
    const canonical = postExists ? substackUrl : newsletterBase;

    // Same HTML served to everyone. Crawlers parse the meta tags and
    // ignore <meta http-equiv="refresh"> and <script> — they don't
    // execute either. Humans get redirected immediately by both.
    const doc = `<!DOCTYPE html>
<html><head>
<meta charset="utf-8">
<title>${esc(title)}</title>
<link rel="canonical" href="${esc(canonical)}">
<meta name="robots" content="noindex, nofollow">

<meta property="og:type" content="article">
<meta property="og:url" content="${esc(canonical)}">
<meta property="og:title" content="${esc(title)}">
<meta property="og:description" content="${esc(description)}">
${image ? `<meta property="og:image" content="${esc(image)}">
<meta property="og:image:width" content="1200">
<meta property="og:image:height" content="630">` : ""}

<meta name="twitter:card" content="summary_large_image">
<meta name="twitter:title" content="${esc(title)}">
<meta name="twitter:description" content="${esc(description)}">
${image ? `<meta name="twitter:image" content="${esc(image)}">` : ""}

<meta http-equiv="refresh" content="0; url=${esc(effectiveTarget)}">
</head>
<body style="background:#fff;font-family:system-ui;padding:2rem;visibility:hidden">
<script>location.replace(${JSON.stringify(effectiveTarget)});</script>
<p><a href="${esc(effectiveTarget)}">Continue →</a></p>
</body></html>`;

    const resp = new Response(doc, {
      status: 200,
      headers: {
        "content-type": "text/html; charset=utf-8",
        "cache-control": "public, max-age=300, s-maxage=300",
        "x-robots-tag": "noindex, nofollow",
      },
    });
    ctx.waitUntil(cache.put(cacheKey, resp.clone()));
    return resp;
  },
};
```