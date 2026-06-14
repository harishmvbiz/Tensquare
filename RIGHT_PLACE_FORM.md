# Tensquare — "Are We the Right Place?" Form (Context & Reference)

A reference for the interactive qualifier form added to the **homepage**. Keep it with the project alongside `SITE_CONTEXT.md` and `TENSQUARE_WEBSITE_GUIDE.md`.

---

## 1. What it is

A friendly, 3-step interactive form on the home page (`index.html`) that qualifies visitors before they enquire. It checks whether what they need matches Tensquare's services, tells them on the spot, and — if it's a fit — collects their details and submits them. A small animated **guide arrow** points the visitor to the next action at every step.

It lives in its own section: `<section id="right-place">`, placed just under the hero stats.

## 2. How it flows

**Step 1 — "What do you need help with?"**
A grid of 10 buttons. Five are Tensquare's actual services (aligned 1:1 with the Services Hub); five are common areas Tensquare does *not* cover, interleaved so the check is meaningful.

| In the right place (we do this) | Not our area (we don't) |
|---|---|
| Business Advisory | Legal advice |
| Accounting | Mortgage & lending |
| Tax Compliance | Investments & planning |
| Bookkeeping | Insurance |
| Finance | Web & marketing |

- Pick **one of ours** → green message: *"You're in the right place. We handle [service] every day…"* and the **Continue** button unlocks (and gently pulses).
- Pick a **non-service** → amber message: *"This isn't quite the right place for that…"*, the button is highlighted in gold, and **Continue stays locked** until they choose a real service. This is the "right place / not the right place" logic you asked for.

**Step 2 — "And you're a…?"**
Individual / Sole trader / Business or Company / Not sure yet. Personalises the enquiry.

**Step 3 — "Where do we send your answer?"**
Confirms their selection (*"You're asking about [service] — [type]."*), then collects **name, email, phone (optional)** and an optional message, and **Submits**.

**Done**
A success panel: *"You're in the right place, [name]!"* with their chosen service noted, a WhatsApp shortcut, and a "Start over" button.

## 3. The guiding arrow

Each step shows an animated pill (e.g. **"👉 Pick what you need"**) with a bouncing arrow that draws the eye to the choices/next action. It changes wording per step ("Tell us who you are", "Where do we send your answer?"). When a valid service is chosen, the **Continue** button also pulses to guide the next tap.

## 4. Where the data goes

Submissions use the **same Web3Forms key** as the contact form and chatbot. The payload includes: name, email, phone, **selected service**, **client type**, message, and a `source` of "Homepage right-place form", with the subject line *"Right-place enquiry — [service] ([name])"*.

- **Until you add your key:** the form runs in **demo mode** — it shows the success panel but sends nothing (a safe placeholder). 
- **After you add your key** (replace `YOUR_WEB3FORMS_ACCESS_KEY` — see the main guide §6): real submissions arrive in your inbox automatically. No extra setup; it's the one key for the contact form, newsletter, chatbot and this form.

## 5. Editing it later

- **Change the service options or the "not us" list:** they're defined together in the build in a single list (`RP_OPTIONS`) and rendered into `index.html`. In the page itself, look for buttons with `data-fit="yes"` (our services) and `data-fit="no"` (not our area) inside `id="right-place"`. Add/remove a `<button class="rp-opt" data-fit="…" data-svc="…">…</button>` line to adjust. Keep the `data-fit` value correct so the right/not-right logic stays accurate.
- **Change the messages:** the green/amber wording lives in the inline script for the right-place section (search the page for `You\u2019re in the right place` / `This isn\u2019t quite`).
- **Change client types:** edit the Step 2 buttons (`data-who="…"`).
- **Styling:** all visuals are controlled by the `.rp-*` classes in `shared.css` (progress bar, option buttons, the guide pill animation, feedback colours, the done state).

## 6. Accessibility & responsiveness

- Keyboard-operable buttons, `aria-live` feedback region, and progress label.
- Fully responsive: two-column on desktop, single column on tablet/mobile (breakpoint at 860px). Verified on desktop, tablet and a 390px mobile viewport.
- Works with the site's light/dark themes and the accessibility panel.

## 7. Validation performed

After adding the form the whole site was validated **three times** (links, anchors, JS handler targets, balanced tags, alt text, CSS variables, leftover tokens, JS brace balance) — zero issues each time — plus a headless-browser test that drove the form end to end:
- wrong selection → not-right message + Continue stays disabled ✓
- right selection → right message + Continue enabled ✓
- step navigation (forward/back) ✓
- empty submit → validation error ✓
- valid submit → personalised success panel ✓
- start-over reset ✓
- no JavaScript errors on any page ✓

Re-run `validate.py` and the browser checks after any future edit.

---

*Reference for Tensquare Accounting & Tax. ABN 20 772 623 135.*
