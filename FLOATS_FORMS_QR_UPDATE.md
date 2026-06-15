# Tensquare — Floats, Forms & QR (Context, this revision)

This revision was built **on the version you uploaded** (`Raw_files.zip`), keeping it simple and changing only what was asked. Keep this note with the other project docs.

## What this version keeps (from your uploaded base)
- **WhatsApp & Email floating buttons still open their in-page enquiry forms** (the little message panels), exactly as before — clicking them does **not** jump straight to WhatsApp/email. This was your main request: those forms are back.
- All existing pages, content, navigation, popups and behaviour are unchanged.

## What was added / fixed
1. **Digital Business Card floating button (new).** A third floating button (gold, QR icon) now sits under WhatsApp and Email. Tapping it opens the digital business card page (`business-card.html`).
2. **Floating buttons are icon-only — no stray text.** The "WhatsApp us / Email us / Business card" text that was leaking onto the page in the other version is gone. The buttons show just their icons (with hover tooltips), so nothing can spill onto the page even if styling is ever cached.
3. **Form field colours fixed (theme-aware).** The dropdown menus (e.g. "What do you need help with?") were showing near-invisible options. All form fields — inputs, text areas and dropdown options — now use readable colours that follow the active theme:
   - Dark theme: light text on a dark field/menu.
   - Light theme: dark text on a white field/menu.
   This is applied site-wide, so every form (contact, newsletter, the homepage qualifier) is consistent.
4. **QR code kept working on iPhone, Android & Google Lens.** Your uploaded base still had the old line-ending bug in the QR. This revision keeps the corrected version: the on-screen QR is a verified contact-card QR (valid CRLF vCard with a structured name field) that decodes on all phones. "Save contact / Download" delivers the full card (including address) via the `.vcf` file.
5. **Caching fixed so updates actually show.** The site previously told browsers/Cloudflare to hold the stylesheet for 7 days, which is why edits didn't appear after deploying. Now the HTML and stylesheet **always revalidate**, and the stylesheet link is version-tagged (`shared.css?v=2`), so future updates appear immediately. Images stay cached for speed.

## Validation performed
- Custom validator run **3×, zero issues**: every internal link/asset resolves; all 14 pages have the 3 floating buttons including the business-card link; the WhatsApp/Email popups are intact; no leaking label text anywhere; the stylesheet is cache-busted; the form-colour fix is present.
- Headless browser test across **all 14 pages: no JavaScript errors**; theme toggle, accessibility panel, and both the WhatsApp and Email enquiry popups open correctly.
- The business-card QR (and the standalone QR file and `.vcf`) were **decoded to confirm** they're valid CRLF contact cards.

## Deploying this update
1. Push these files to your GitHub repo (Cloudflare Pages auto-deploys).
2. In Cloudflare: **Caching → Configuration → Purge Everything** once, so the old stylesheet/QR are dropped from the edge.
3. Hard-refresh on your phone (or reopen the tab). You should see: the gold business-card float, readable dropdowns, the WhatsApp/Email forms working, and the QR adding a contact on both iPhone and Android.

---
*Tensquare Accounting & Tax · ABN 20 772 623 135.*
