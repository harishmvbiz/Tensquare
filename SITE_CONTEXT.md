# Tensquare Website — Site Context & Reference

A technical reference for this website. Keep it with the project. It explains how the site is put together, where everything lives, what's a placeholder, and how to extend it later. Pair it with `TENSQUARE_WEBSITE_GUIDE.md` (the step-by-step hosting/how-to).

---

## 1. What this is

A hand-built, dependency-free **static website** — plain HTML, one CSS file, and vanilla JavaScript. No build step, no framework, no server required. It can be hosted by dropping the folder onto any static host (Netlify, Cloudflare Pages, GitHub Pages, or even plain web hosting).

- **14 HTML pages** + `shared.css` + assets.
- Fully responsive (PC, desktop, tablet, mobile) via CSS breakpoints at 1680, 1500 (large), 980, 760 and 480 px.
- Light/dark themes, accessibility controls, and all preferences saved in the browser's `localStorage`.

## 2. Business details (single source of truth)

These appear throughout the site. If they change, update everywhere (use "Replace in Files"):

| Field | Value |
|---|---|
| Business | Tensquare Accounting & Tax |
| Founder | Arun Kalluparampil — Principal & Founder, CPA |
| Phone | 0431 533 623 (intl +61 431 533 623) |
| WhatsApp number | `61431533623` |
| Email | arun@tensquare.com.au |
| Address | 16/20 Neiwand Street, Calamvale QLD 4116 |
| ABN | 20 772 623 135 |
| Assumed domain | https://tensquare.com.au |
| Region served | Australia only |

> Per the founder's instruction, **no current or past employer is mentioned** anywhere. Keep it that way unless you decide otherwise.

## 3. Page map

| File | Purpose |
|---|---|
| `index.html` | Home |
| `services.html` | Services Hub — 5 anchored sections: `#advisory #finance #accounting #bookkeeping #tax` |
| `about.html` | Our Story |
| `team.html` | Founder bio + role-based capability cards |
| `insights.html` | Blog index |
| `post-tax-time-2026.html` / `post-bas-bookkeeping.html` / `post-business-structure.html` | Articles |
| `testimonials.html` | Client Stories — **sample** testimonials (labelled) |
| `contact.html` | Contact form + details + Google Maps embed |
| `business-card.html` | Digital business card + QR + vCard download |
| `privacy.html` / `terms.html` | Legal |
| `404.html` | Not-found page |
| `sitemap.xml`, `robots.txt`, `_headers`, `netlify.toml` | SEO + host config |
| `arun-kalluparampil.vcf` | Downloadable contact card |
| `qr-arun.png` | Backup QR image (also embedded inline on the card page) |

## 4. Design system (`shared.css`)

- **Brand colours** and fonts are defined as CSS variables in the `:root` block at the top (royal blue `#1F3BD6`, electric `#1A1AF0`, azure `#2FA6F0`, deep navy, CPA gold `#E8B30B`). Dark and light theme tokens are both there.
- **Fonts:** Sora (display), Inter (body), IBM Plex Mono (labels) — loaded from Google Fonts.
- **Container width:** controlled by `--maxw` (1340px default; 1500px ≥1700px screens; 1680px ≥2200px). Increase/decrease there to change how wide the content sits.
- **Signature element:** the glass "10²" diamond (hero + cards). The logo mark is an inline SVG generated in code — no image file needed.
- **Key component classes:** `.hero`, `.section`, `.card.glass`, `.grid.g2/.g3/.g4`, `.btn.btn-primary/.btn-ghost`, `.svc-visual/.svc-ic` (service tiles), `.dbc-*` (business card), `.cbot-*` (chatbot), `.socials` (footer social icons), `.prose.justify` (justified article/bio text).

## 5. JavaScript (all inline, vanilla)

The same `<script>` block is included on every page (it's generated once and appended at build). It handles:

- Theme toggle, accessibility panel (text-size via `--a11y-fs`, grayscale, underline-links, reduce-motion), all saved under `tsq-*` keys in `localStorage`.
- Mobile menu, dropdowns, go-to-top.
- WhatsApp & email float popups (guided message builder → redirects to `wa.me` / `mailto`).
- Newsletter + contact form submit (Web3Forms).
- The **Tensq chatbot** (see §7).
- Smooth in-page anchor scrolling with header offset.

## 6. Placeholders to replace before/after launch

| Placeholder | Where | Replace with |
|---|---|---|
| `YOUR_WEB3FORMS_ACCESS_KEY` | all 14 HTML files (inline script) | your free Web3Forms key (powers the contact form, newsletter **and** chatbot leads) |
| `linkedin.com/company/tensquare-accounting-tax` | footer | real LinkedIn URL |
| `facebook.com/tensquareaccounting` | footer | real Facebook URL |
| `instagram.com/tensquareaccounting` | footer | real Instagram URL |
| `x.com/tensquare_au` | footer | real X URL |
| Sample testimonials | `testimonials.html` | real, consented reviews (remove the "Sample" tag) |

Everything else (phone, email, address, ABN, QR, vCard) is real and ready.

## 7. The Tensq chatbot — how it works

- **Markup:** a launcher button `#cbotLaunch` and a panel `#cbotPanel` (with `#cbotBody`, `#cbotInput`, `#cbotSend`), present on every page. Styled by the `.cbot-*` rules in `shared.css`.
- **Logic:** a small rule-based conversation in the inline script. Quick replies route to canned helpful answers; free text or "book"/"tax" flows trigger a **lead capture** that collects name → email → enquiry.
- **Delivery:** on completion it submits to **Web3Forms** using the same key as the contact form, subject "Tensq chatbot lead". If the key is still the placeholder, it runs in **demo mode** (shows a confirmation + a note, sends nothing) and still offers WhatsApp/email/contact links.
- **To extend into a real AI bot later:** keep `#cbotPanel`/`#cbotBody` and replace the `userText()` / `handleIntent()` functions with calls to your chosen chatbot API. The UI won't need to change.

## 8. The QR / digital business card

- The QR encodes a compact vCard (~243 bytes, version 11) so phone cameras prompt "save contact". The page **regenerates the QR live** in the browser via a CDN library, with the bundled PNG as an offline fallback. The downloadable `.vcf` is richer (includes a structured name field).
- If contact details change, regenerate both the `.vcf` and the QR. The vCard text format is visible by opening `arun-kalluparampil.vcf` in any text editor.

## 9. Honesty & compliance notes

- No fabricated reviews or statistics presented as real. Numbers shown (e.g. "5 service areas") are factual. Testimonials are labelled "Sample" until replaced.
- Articles carry "general information / not advice" disclaimers. Legal pages align with the Australian Privacy Act 1988 and APPs but should be reviewed for your exact practices.
- The chatbot states it is "not financial advice".

## 10. Validation performed

Before delivery the site was validated multiple times for: internal links, in-page anchors, every JavaScript handler target, balanced HTML tags, image alt text, defined CSS variables, leftover template tokens, and JS brace/paren balance — plus a headless browser pass exercising every toggle, popup and the chatbot across all 14 pages with no JavaScript errors. Re-run the same checks after any future edit.

---

*Reference file for Tensquare Accounting & Tax. ABN 20 772 623 135.*
