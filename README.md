# DeReset Brand Hub — Step 4.5 Deploy Package v3 (Footer/Nav — Contact link fix)

**Status:** Ready to deploy — fixes a real navigation gap you caught
**Date:** 2026-09-18

## Why there's a "v3"

You spotted it: the Contact page wasn't reachable from the homepage, the header nav, or the footer on any page — the only way in was clicking through from a link buried inside the Privacy or Terms page text. That's a real gap in the shared header/footer, not a design choice.

Cause: the shared footer only linked Privacy, Terms, and a plain `mailto:` address — never `/contact`. The shared header nav only had "Products". Since your homepage (`index.html`) uses that same shared header and footer, this bug affects the homepage too, not just the three legal pages.

## What's different in this package

- `privacy.html`, `terms.html`, `contact.html` — **footer updated**: the old `mailto:support@dereset.com` text link is now a proper `Contact` link to `/contact`. **Header nav updated**: added a `Contact` link next to `Products`, so Contact is reachable from every page, not just from inside Privacy/Terms.
- No legal wording changed. No layout, styling, or CSP-related files changed — this is a links-only fix.
- `styles/legal.css` — unchanged, not included in this package (you already have it from v2).
- `index.html` — **needs the same fix, but isn't included as a file here.** I don't have a verified current copy of your live `index.html` in this session, so rather than risk uploading a stale version over your real homepage, Part 2 below gives you a small, safe copy-paste edit to make directly on GitHub.

## How to install this (step-by-step)

**Part 1 — Replace the three legal pages**

1. Go to **github.com**, sign in, and open your `dereset-hub` repository.
2. Click **Add file** → **Upload files**.
3. Drag in `privacy.html`, `terms.html`, and `contact.html` from this package. GitHub will recognize these as the same filenames already in the repo and overwrite them when you commit.
4. Scroll down and click **Commit changes**.

**Part 2 — Fix the homepage's header and footer directly on GitHub**

5. From your repository's main file list, click on **`index.html`**.
6. Click the **pencil icon** (Edit this file) near the top right of the file view.
7. Use your browser's find function (Ctrl+F / Cmd+F won't search inside GitHub's editor — instead just look for the lines described below) to find the navigation line inside the `<header class="site-header">` section. It will look like this:

   ```html
   <a class="nav-link" href="/#products">Products</a>
   ```

   Right after that line, add a new line so it reads:

   ```html
   <a class="nav-link" href="/#products">Products</a>
   <a class="nav-link" href="/contact">Contact</a>
   ```

8. Scroll down to the `<footer class="site-footer">` section near the bottom. Find the line that looks like this (yours may end in `support@dereset.com</a>` from a `mailto:` link, or may already differ slightly — match on the overall shape):

   ```html
   <p>&copy; 2026 DeReset &middot; <a href="/privacy">Privacy Policy</a> &middot; <a href="/terms">Terms of Service</a> &middot; <a href="mailto:support@dereset.com">support@dereset.com</a></p>
   ```

   Replace it with:

   ```html
   <p>&copy; 2026 DeReset &middot; <a href="/privacy">Privacy Policy</a> &middot; <a href="/terms">Terms of Service</a> &middot; <a href="/contact">Contact</a></p>
   ```

9. Scroll to the bottom of the editor, add a short commit message (e.g. "Add Contact link to header/footer"), and click **Commit changes**.

If your live `index.html`'s footer/header text doesn't match what's shown above exactly (for example if you've made other edits since), just add the `Contact` link in the same style as the existing `Privacy Policy` / `Terms of Service` links — don't paste over anything you don't recognize. If you're unsure, paste me the current header/footer section of your live `index.html` and I'll give you an exact match.

10. Cloudflare Pages will redeploy automatically. Give it 1–2 minutes.

## Post-deploy checklist

- [ ] Homepage header shows a "Contact" link next to "Products"
- [ ] Homepage footer shows Privacy Policy · Terms of Service · Contact
- [ ] Same header/footer links appear correctly on `/privacy`, `/terms`, and `/contact`
- [ ] Clicking "Contact" from the homepage lands on `/contact` and looks fully styled (from the v2 fix)
- [ ] No leftover `mailto:` link needed — the Contact page itself has the gold "email us" button
