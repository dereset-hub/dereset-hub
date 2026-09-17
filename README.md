# DeReset Brand Hub — Step 4.4 Static Package (Merged, Decision 005 logo update)

**Status:** Source ready for deploy — not yet production-verified  
**Date:** 2026-09-17 (logo swap applied same day, post Decision 005)

## Decision 005 — Header logo swap (2026-09-17)

Header wordmark changed from the light-transparent variant to the **dark wordmark**, on the same cream header background. This supersedes the "Critical fix #1" pairing described below and the LOCKED usage rule in `04-Design-System-and-Brand-Assets.md`. See the platform project's Decision Log (Decision 005) for the full DETECT → RECOMMEND → APPROVE record. Only `index.html` changed — no asset files were added or removed; both wordmark PNGs remain in `/assets/` for future use.

## What this is

Production-ready static source for `dereset.com` (Cloudflare Pages project `dereset-hub`).

Merged from:
- Platform-built package (tokens, full favicon set, light wordmark on cream header, sticky header)
- External Step 4.4 package (dark charcoal hero, editorial type scale, skip-link, 404, robots, simpler footer)

## Critical fixes applied in merge

1. **Logo contrast** — External package placed the *dark* wordmark on the charcoal hero/header context. Merged package uses the **light transparent wordmark** on the cream sticky header (correct pairing per locked design system).
2. **Full favicon set** — Android Chrome 192/512 restored.
3. **Font loading** — Playfair Display + Poppins loaded via Google Fonts CDN for v1 (loading method still TODO in design system).
4. **No invented claims** — All product cards remain “Coming soon”; no live links, pricing, or status over-claims.
5. **No fake legal links** — Footer is structural only (© + tagline).

## Deploy contract

| Field | Value |
|-------|-------|
| Rendering | Static HTML/CSS |
| Framework | None |
| Build command | *(blank)* |
| Output directory | `/` (repository root) |
| JS | None required for v1 |
| Analytics | Deferred to Step 4.6 |
| Security headers | Deferred to Step 4.7 (`_headers`) |

## Install into Pages repo

Copy the contents of this folder to the root of `dereset-hub/dereset-hub` (or equivalent), replacing the placeholder. Commit and push to the production branch.

## Post-deploy QA checklist

- [ ] https://dereset.com loads this hub (not placeholder)
- [ ] Logo readable on cream header
- [ ] Favicons appear in browser tab
- [ ] Mobile layout (product grid stacks)
- [ ] Keyboard: skip link appears on focus; focus rings visible
- [ ] 404 page works for unknown paths
- [ ] No console errors for missing assets

## Out of scope (later steps)

- Footer legal URLs/copy (4.5)
- Cloudflare Web Analytics (4.6)
- `_headers` security baseline (4.7)
- Product live links (only when subdomain verified + AI DPL OS bridge if needed)
