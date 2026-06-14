# Tensquare — Floats, Mobile Hero & Shareable Business Card (Context)

Reference for the changes made in this round. Keep alongside the other project docs (`SITE_CONTEXT.md`, `RIGHT_PLACE_FORM.md`, the go-live and security guides).

---

## 1. Mobile / tablet hero fixed
**Problem:** on phones and tablets the rotating "10²" diamond visually overlapped the "Clear advice…" heading.

**Cause:** the diamond's rings are squares rotated 45°. A full-width square's *diagonal* is ~1.4× its side, so the rotated ring overflowed its own box and bled onto the text below.

**Fix:** the rings are now **inset inside their box** (`.hero-diamond .ring { inset:15% }`, `.r2 { inset:27% }`) so the rotated diamond fits entirely within its container at every screen size — no overflow. Plus size caps were added for tablet (`max-width:980px → diamond ≤330px`) and phones (`max-width:480px → diamond ≤250px`), and the floating "Built around / Standards" cards are hidden below 980px. Verified at 390px, 768px and desktop.

> Also fixed a side bug: the homepage "right place" form used to auto-scroll into view on page load. It now only scrolls when the visitor actually moves between steps.

## 2. Floating buttons — now direct links, no pop-ups
Per the requirement that nothing should rely on pop-ups (some clients block them), the floating action buttons are now **plain links that navigate directly**:

| Button | Action |
|---|---|
| **WhatsApp** (green) | `https://wa.me/61431533623?text=…` — opens WhatsApp app/web with a friendly pre-filled message |
| **Email** (azure) | `mailto:arun@tensquare.com.au?subject=Website enquiry` — opens the visitor's email app |
| **Business card** (gold) | `business-card.html` — opens Arun's digital card |

- The old in-page message-builder pop-ups (and their JavaScript) were **removed entirely**.
- All three are styled as **frosted-glass circular buttons** with a hover label that slides out, and the **WhatsApp button uses the proper WhatsApp logo** in its brand green.
- "Back to top" remains.

## 3. Shareable digital business card (trust-focused)
The card page (`business-card.html`) is built to be shared in WhatsApp groups, communities and social media **without looking like spam**:

- **Branded link preview (Open Graph):** sharing the URL now shows a professional 1200×630 preview image (`og-card.png`) with the Tensquare branding, Arun's name, "Principal & Founder · CPA", contact details, ABN and a scannable QR. This is the single biggest trust signal when a link is pasted into WhatsApp. A general site-wide preview (`og-default.png`) is used on all other pages.
- **Verified-details trust strip** on the card: a "CPA Practice" badge, a "Verified business details" line, a plain statement that this is the official card of Arun Kalluparampil (Principal & Founder) of Tensquare Accounting & Tax — a registered CPA practice in Calamvale QLD — with the **ABN**, **registered address**, a link to verify on **tensquare.com.au**, and the Professional Standards Legislation tagline.
- **Save / share actions:** "Save contact" and "Download .vcf" work offline via a Blob; a native "Share" button appears on mobiles that support the Web Share API; the QR regenerates live in the browser with the bundled PNG as a fallback.

**How to share it:** once live, share **`https://tensquare.com.au/business-card.html`** in any WhatsApp group, bio link or social post. Recipients see the branded preview, can tap to open, then scan the QR or tap "Save contact" to add Arun to their phone.

## 4. Open Graph images — how to update
- Files: `og-card.png` (business card) and `og-default.png` (site-wide), both 1200×630, in the site root.
- They're referenced via `og:image` / `twitter:image` meta tags in each page's `<head>` using absolute URLs (`https://tensquare.com.au/og-…png`).
- If contact details change, regenerate them (the project's `gen_og.py` builds both from the brand colours, Poppins font and the live QR), or have a designer replace the two PNGs at the same dimensions.

## 5. Validation performed
The whole site was validated **three times** (internal links, in-page anchors, JS handler targets, balanced tags, image alt text, CSS variables, leftover tokens, JS brace balance) — **zero issues each time** — and a headless-browser pass confirmed:
- no auto-scroll on load; WhatsApp/Email/Card float links resolve correctly; **no pop-up elements remain**;
- theme toggle, accessibility panel, chatbot open/close all work; the "right place" form still blocks/permits Continue correctly;
- **no JavaScript errors** on any page; layouts verified on phone (390px), tablet (768px) and desktop.

---

*Reference for Tensquare Accounting & Tax. ABN 20 772 623 135.*
