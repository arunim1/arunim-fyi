# arunim.fyi (deploy archive)

This repo holds — and serves — the static site behind **[arunim.fyi](https://arunim.fyi)** — Arunim's digital garden of notes, essays, and research. GitHub Pages serves `docs/` directly.

It's a deploy artifact, not a source repo. The source lives privately. Each commit here is built from the source repo and references the source commit it came from in `.source-commit`.

## Layout

```
.
├── README.md         ← you are here
├── content/          ← unencrypted markdown for public pages
└── docs/             ← rendered site (HTML, JS, CSS, encrypted blobs for private pages) — the Pages source
```

`content/` exists for human-readable diffs — when a public note changes, you see a real markdown diff instead of a re-rendered HTML diff. The `docs/` folder is what arunim.fyi serves.

## Why some pages don't decrypt

Pages without `public: true` in their frontmatter ship as encrypted blobs. They render as a "🔒 This page is locked" placeholder unless you have a passphrase — or a per-page share link. If you're a friend who got a passphrase, type it on the homepage. If someone sent you a link with a `#k=` fragment, it unlocks exactly that one page (and the key it carries expires every couple of months).

Encryption uses libsodium under the hood: Argon2id (m=32 MiB, t=2) for key derivation, XChaCha20-Poly1305 for content + asset encryption, one key per page (wrapped copies published for passphrase holders), deterministic nonces so unchanged content produces byte-identical ciphertext across builds (this repo's diffs stay readable).

## Provenance

`.source-commit` always names the source-repo SHA the current build came from. Commits made from Arunim's machine are signed by his personal SSH signing key (look for the "Verified" badge); scheduled re-key builds are committed unsigned by github-actions[bot] from the private source repo's CI.
