# DeReset Brand Hub — Step 4.5 Deploy Package v2 (Footer Legal — style fix)

**Status:** Ready to deploy — fixes a real bug in the v1 package you already deployed
**Date:** 2026-09-18

## Why there's a "v2"

After you deployed the first Step 4.5 package, you reported that `/privacy`, `/terms`, and `/contact` looked like plain, unstyled HTML with none of the site's identity. That wasn't a cosmetic choice — it was a bug in what I gave you.

Those three pages carried their CSS inside a `<style>` block in the page itself, rather than in a separate `.css` file. Your site's security headers (Decision 006) include a Content-Security-Policy that only allows styling from `'self'` (your own external stylesheet files) — and that same policy blocks embedded `<style>` blocks too, not just inline `style="..."` attributes on individual elements. I checked for the second thing and missed the first, so the whole `<style>` block was silently discarded by the browser, and you got unstyled HTML. My mistake — this package fixes it properly.

## What's different in this package

- `privacy.html`, `terms.html`, `contact.html` — **rebuilt** to use the exact same shared header, footer, and layout as your homepage (`index.html`), pulling their styling from real external stylesheets instead of an embedded `<style>` block. No legal wording changed anywhere — every sentence is still exactly what AI DPL OS approved.
- `styles/legal.css` — **new file.** Holds just the legal-page-specific styling (headings, spacing, the contact button, etc.), reusing your existing color/type/spacing tokens from `dereset-tokens.css`. This is the file that was missing before.
- `index.html` — **unchanged** from what you already deployed. You do not need to touch it again.

## How to install this (step-by-step)

You'll do two things: add one new file, and replace three existing ones.

**Part 1 — Add the new stylesheet**

1. Go to **github.com**, sign in, and open your `dereset-hub` repository.
2. Click into the **`styles`** folder (it already has `dereset-tokens.css` and `site.css` in it from your earlier deploys).
3. Click **Add file** → **Upload files**.
4. Drag in `legal.css` from the `styles` folder of this package (or click "choose your files" and select it).
5. Scroll down and click **Commit changes**.

**Part 2 — Replace the three broken pages**

6. Go back to the repository's main file list (click the repo name at the top, or "dereset-hub" in the breadcrumb).
7. Click **Add file** → **Upload files**.
8. Drag in `privacy.html`, `terms.html`, and `contact.html` from this package's top-level folder. GitHub will recognize these as the same filenames already in the repo and will overwrite them when you commit.
9. Scroll down and click **Commit changes**.
10. Cloudflare Pages will automatically redeploy (same as your last few deploys). Give it 1–2 minutes.

**Do not re-upload `index.html`** — it hasn't changed since your last deploy.

11. To check it worked: visit `https://dereset.com/privacy`, `https://dereset.com/terms`, and `https://dereset.com/contact`. They should now look like proper DeReset pages — the same sticky header and wordmark as the homepage, the same fonts and colors, a readable text column, and a matching footer — not plain black-on-white text.

## Post-deploy checklist

- [ ] `dereset.com/privacy` shows the DeReset header (dark wordmark, cream background) and footer, not a bare unstyled page
- [ ] `dereset.com/terms` and `dereset.com/contact` look the same way
- [ ] Headings are in the serif display font, body text in the sans-serif font, matching the homepage
- [ ] The gold "email us" button appears correctly on the Contact page
- [ ] Links between the three legal pages and back to the homepage work
- [ ] Browser console (right-click → Inspect → Console tab) shows no red CSP errors when visiting any of the three pages — if you're comfortable checking this, it's the most direct confirmation the fix worked

## Out of scope (flagged, not blocking this deploy)

- Product-page footers on Gumroad sales pages still point to Gumroad's generic legal links, not the new DeReset-hosted ones — AI DPL OS flagged this as a follow-up cleanup, not part of this handoff.
- No lawyer has reviewed this content — AI DPL OS's own response noted this and recommended a real review if DeReset's sales grow or a dispute becomes a real possibility.
