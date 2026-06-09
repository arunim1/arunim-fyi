# arunim.fyi (deploy archive)

This repo holds — and serves — the static site behind **[arunim.fyi](https://arunim.fyi)** — Arunim's digital garden of notes, essays, and research. GitHub Pages serves `docs/` directly.

It's a deploy artifact, not a source repo. The source lives privately. Each commit here is built locally from the source repo and references the source commit it came from in `.source-commit`.

## Layout

```
.
├── README.md         ← you are here
├── content/          ← unencrypted markdown for public pages
└── docs/             ← rendered site (HTML, JS, CSS, encrypted blobs for private pages) — the Pages source
```

`content/` exists for human-readable diffs — when a public note changes, you see a real markdown diff instead of a re-rendered HTML diff. The `docs/` folder is what arunim.fyi serves.

## Why some pages don't decrypt

Pages without `public: true` in their frontmatter ship as encrypted blobs. They render as a "🔒 This page is locked" placeholder unless you have a passphrase. If you're a friend who got one, type it on the homepage — the rest of the garden becomes readable for ten minutes.

Encryption uses libsodium under the hood: Argon2id (m=32 MiB, t=2) for key derivation, XChaCha20-Poly1305 for content + asset encryption, deterministic nonces so unchanged content produces byte-identical ciphertext across builds (this repo's diffs stay readable).

## Provenance

`.source-commit` always names the source-repo SHA the current build came from. Each commit on this repo is signed by Arunim's personal SSH signing key — look for the "Verified" badge on github.com. History starts 2026-06-09 — the repo was reset to a fresh root commit when it went public.
