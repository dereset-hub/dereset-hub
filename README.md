# DeReset Brand Hub — Step 4.5 Deploy Package (Footer Legal)

**Status:** Ready to deploy — AI DPL OS-approved content, platform-level QA applied
**Date:** 2026-09-18

## What's in this package

Four files, all going to the root of the `dereset-hub` repo:

- `index.html` — the existing hub homepage, with one change: the footer now links to Privacy Policy, Terms of Service, and a support email, instead of being copyright-only.
- `privacy.html` — new. Will be reachable at `dereset.com/privacy`.
- `terms.html` — new. Will be reachable at `dereset.com/terms`.
- `contact.html` — new. Will be reachable at `dereset.com/contact`.

(Cloudflare Pages automatically serves `privacy.html` at the clean URL `/privacy` — you don't need to rename anything or create folders.)

## What changed and why

AI DPL OS approved and supplied real Privacy Policy, Terms of Service, and Contact page content for DeReset (entity name, support email, refund policy, data-handling disclosures — see `05-Decision-Log.md` Decision 007 for the full record). Two small technical adjustments were made before packaging, both under this platform project's own authority (shared design system + security headers), not new content decisions:

1. **Typography aligned to the locked DeReset design system.** The supplied pages used a generic serif font throughout. Switched headings to Playfair Display and body text to Poppins — the same fonts already used on the homepage — so the new pages look like part of the same site rather than a separate document.
2. **Removed two inline `style="..."` attributes on the Contact page.** The site's security headers (Decision 006) block inline styles via Content-Security-Policy — this is intentional and not being changed. Those two small styling rules were moved into the page's own `<style>` block as CSS classes instead, so they render correctly without weakening the security policy.

No legal wording was changed. No dollar amounts, entity names, policy terms, or dates were altered from what AI DPL OS supplied.

## How to install this (step-by-step, no prior GitHub experience needed)

This uses the same method you've used for the last two deploys.

1. Go to **github.com** and sign in.
2. Open your `dereset-hub` repository (the one connected to Cloudflare Pages — it's the repo you uploaded `index.html` to before).
3. You'll see a file list. Click on **`index.html`** in that list to open it.
4. Click the **pencil icon** (Edit this file) in the top-right of the file view.
5. Select all the text in the editor (click inside it, then press `Ctrl+A` on Windows/Linux or `Cmd+A` on Mac) and delete it.
6. Open the `index.html` file from **this package** on your computer in a plain text editor (Notepad, TextEdit, VS Code — anything that shows raw text, not Word), select all its contents, copy them, and paste them into the GitHub editor.
7. Scroll down, and under "Commit changes," leave the default message (or type something like "Step 4.5: footer legal links") and click **Commit changes**.
8. Now go back to the repository's main file list. Click the green **Add file** button, then **Upload files**.
9. Drag in the three new files from this package — `privacy.html`, `terms.html`, `contact.html` — or click "choose your files" and select them.
10. Scroll down and click **Commit changes**.
11. Cloudflare Pages will automatically pick up both commits and redeploy (you've seen this happen automatically the last two times). Give it 1–2 minutes.
12. To check it worked: visit `https://dereset.com/privacy`, `https://dereset.com/terms`, and `https://dereset.com/contact` in your browser, and check that the homepage footer now shows the new links.

That's it — same process as before, just four files this time instead of one.

## Post-deploy checklist

- [ ] `dereset.com/privacy` loads and shows the Privacy Policy
- [ ] `dereset.com/terms` loads and shows the Terms of Service
- [ ] `dereset.com/contact` loads and shows the Contact page
- [ ] Homepage footer shows Privacy Policy / Terms of Service / email links
- [ ] Links between the three legal pages and back to the homepage work
- [ ] Fonts look consistent with the rest of the site (headings in the serif display font, body in the sans-serif font)
- [ ] No visibly broken/unstyled elements on the Contact page (the inline-style fix should be invisible — page should look identical to how it did before the CSP fix)

## Out of scope (flagged, not blocking this deploy)

- Product-page footers on Gumroad sales pages still point to Gumroad's generic legal links, not the new DeReset-hosted ones — AI DPL OS flagged this as a follow-up cleanup, not part of this handoff.
- No lawyer has reviewed this content — AI DPL OS's own response noted this and recommended a real review if DeReset's sales grow or a dispute becomes a real possibility.
