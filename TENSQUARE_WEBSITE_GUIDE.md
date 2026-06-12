# Tensquare Accounting & Tax — Website Guide

**Your complete, plain-English handbook for launching and maintaining your website.**

This guide assumes no technical background. Follow it top to bottom and you'll have a live website at very low (or zero) cost. Keep this file — it's your reference for everything.

---

## 1. What you've received

A complete, ready-to-host website. Everything is in the website folder:

| File / type | What it is |
|---|---|
| `index.html` | Home page |
| `services.html` | Services Hub (all 5 services with anchor links) |
| `about.html` | About / Our Story |
| `team.html` | Our Team (founder + capability cards) |
| `insights.html` + 3 `post-*.html` | Blog index and three articles |
| `testimonials.html` | Client Stories (sample testimonials — see §7) |
| `contact.html` | Contact form, details and map |
| `business-card.html` | Digital business card with QR code |
| `privacy.html`, `terms.html`, `404.html` | Legal pages + "page not found" page |
| `shared.css` | The single stylesheet that controls all design (colours, fonts, layout) |
| `arun-kalluparampil.vcf` | The downloadable contact card |
| `qr-arun.png` | A backup QR code image |
| `sitemap.xml`, `robots.txt` | Help Google find and index your site |
| `_headers`, `netlify.toml` | Optional security/hosting settings (used by Netlify & Cloudflare) |

Everything uses **relative links**, which means the site works no matter where you host it — no configuration needed.

---

## 2. Quick preview on your own computer

Before publishing, you can look at the site locally:

1. Find the website folder on your computer.
2. Double-click **`index.html`**.
3. It opens in your web browser. Click around — every page and button works.

> Note: when previewing this way, the **contact form** and **newsletter** will show a friendly "demo" message instead of actually sending. That's expected until you add a free Web3Forms key (see §6). The QR code, WhatsApp, email links, theme switch and menus all work fully in preview.

---

## 3. Get your domain name (tensquare.com.au)

A domain is your web address. The site is built assuming **tensquare.com.au**.

- **Where to buy:** an Australian registrar such as **VentraIP**, **Crazy Domains**, **Netregistry**, or **GoDaddy AU**. A `.com.au` typically costs roughly **AUD $15–25 per year**.
- **Requirement:** to register a `.com.au` you need an **ABN** — you have one (ABN 20 772 623 135), so you're eligible.
- You don't need to buy hosting from the registrar. You only need the domain. Hosting is covered next, and it's free.

> If you don't want a custom domain yet, you can still launch immediately on a free address like `tensquare.netlify.app` and add the real domain later.

---

## 4. Publish your website (free options)

Pick **one** of these. **Netlify Drop is the easiest** and takes about two minutes.

### Option A — Netlify Drop (recommended, no account needed to start)
1. Go to **https://app.netlify.com/drop**
2. Drag your **entire website folder** onto the page.
3. Wait a few seconds — your site is live at a temporary address like `random-name-123.netlify.app`.
4. To keep it and add your domain, create a free account when prompted, then go to **Site settings → Domain management → Add custom domain** and enter `tensquare.com.au`. Netlify shows you the DNS records to enter at your domain registrar.

### Option B — Cloudflare Pages (free, great performance)
1. Create a free account at **https://pages.cloudflare.com**
2. Choose **"Upload assets"** (the direct-upload option) and upload your website folder.
3. Follow the prompts to connect `tensquare.com.au`.

### Option C — GitHub Pages (free)
1. Create a free account at **https://github.com**
2. Create a new repository, upload all the website files into it.
3. Go to **Settings → Pages**, set the source to your main branch, and save. Your site publishes at `yourname.github.io/repo`. A custom domain can be added in the same screen.

### Connecting your domain (all options)
After adding your domain in the host, you'll update two settings at your **registrar** (where you bought the domain): the host gives you the exact values to copy. This usually means setting a **CNAME** (or an **A record**) to point at the host. Changes can take a few minutes to a few hours to take effect. **HTTPS (the padlock) is automatic and free** on all three hosts.

---

## 5. WhatsApp & email — already set up

These work out of the box, no accounts or paid tools required:

- **WhatsApp button** (bottom-right green circle): opens a chat to **+61 431 533 623** with a friendly pre-written message. It uses WhatsApp's official `wa.me` link, which works on mobile (opens the app) and desktop (opens WhatsApp Web).
- **Email button** (bottom-right blue circle): opens the visitor's email app with a pre-filled message to **arun@tensquare.com.au**.
- Phone, email and address links throughout the site all work.

**To change the WhatsApp number or email later:** they appear in the page files. The simplest way is a "Find & Replace across files" in a free editor like **VS Code** (see §9):
- WhatsApp number is stored as `61431533623`
- Email is stored as `arun@tensquare.com.au`

---

## 6. Turn on the contact form & newsletter (free — 5 minutes)

The contact form and newsletter are pre-wired to **Web3Forms**, a free service that emails you submissions. No server or coding needed.

**Steps:**
1. Go to **https://web3forms.com**
2. Enter the email address where you want to receive enquiries (e.g. `arun@tensquare.com.au`) and click to get your **Access Key**. It's free and arrives instantly.
3. Copy the access key (a long string of letters and numbers).
4. In every `.html` file, find this exact text:
   ```
   YOUR_WEB3FORMS_ACCESS_KEY
   ```
   and replace it with your real key.

> **Important:** the key appears in **all 14 HTML files** (each page carries the same small script). The easy way to update them all at once is a **"Replace in Files"** / **"Replace All"** across the folder in VS Code (see §9). Search for `YOUR_WEB3FORMS_ACCESS_KEY`, replace with your key, click "Replace All".

5. Save the files and re-upload to your host.
6. Test by submitting the contact form — the enquiry should arrive in your inbox.

Until you do this, the form still works for visitors but shows a polite "demo" message and points them to WhatsApp/email instead. Nothing is broken in the meantime.

---

## 6b. Social media handles (footer)

The footer on every page now shows social icons: **LinkedIn, Facebook, Instagram, X (Twitter)** and **WhatsApp**. The WhatsApp link is real (it points to +61 431 533 623). The others currently use **placeholder addresses** that you should update to your real profiles:

| Network | Placeholder in the files | Replace with |
|---|---|---|
| LinkedIn | `linkedin.com/company/tensquare-accounting-tax` | your LinkedIn page |
| Facebook | `facebook.com/tensquareaccounting` | your Facebook page |
| Instagram | `instagram.com/tensquareaccounting` | your Instagram handle |
| X (Twitter) | `x.com/tensquare_au` | your X handle |

Update them the same way as the form key (§9, "Replace in Files"). If you don't use a network, simply delete that one `<a ...>...</a>` line from the footer. The footer is generated for every page, so a find-and-replace updates them all at once.

## 6c. The "Tensq" chatbot

Every page has a floating **"Chat with Tensq"** assistant (bottom-right). Tensq greets visitors, offers quick options (services, book a consultation, tax question, talk to a human), and can **capture a lead** — it collects the visitor's name, email and enquiry in a friendly conversation.

- **Right now (demo mode):** Tensq runs entirely in the browser. When someone completes the mini-form, it shows a confirmation and a note that it isn't connected yet. Nothing is lost — visitors are also given your WhatsApp, email and contact-page links.
- **To make it deliver leads to your inbox:** Tensq uses the **same Web3Forms key** as the contact form. As soon as you complete §6 (replace `YOUR_WEB3FORMS_ACCESS_KEY`), Tensq's captured leads are emailed to you automatically, with the subject line "Tensq chatbot lead". No extra setup.
- **Later upgrade (optional):** if you ever want a smarter, AI-powered bot, the launcher and panel are already built — a developer can connect it to a chatbot service without changing the design. The `SITE_CONTEXT.md` file explains exactly where the chatbot lives in the code.

---

## 7. Replace the sample testimonials with real ones

To stay honest and compliant, the **Client Stories** page uses clearly-labelled **"Sample"** testimonials — they are *not* presented as real reviews. Replace them as you collect genuine, consented feedback.

**Where:** open `testimonials.html` in a text editor and find the section with the testimonial cards (search for the word `Sample`). Each card looks like this:

```html
<div class="card glass quote">
  <span class="sample-tag"> ... Sample</span>
  <div ...>★★★★★</div>
  <p ...>&ldquo;Their quote goes here&rdquo;</p>
  <div ...>
    <div ...>Client name or role</div>
    <div ...>Their context</div>
  </div>
</div>
```

For a **real** testimonial:
1. Replace the quote text with the client's words.
2. Replace the name/role and context.
3. **Delete this line** so it's no longer marked as a sample:
   ```html
   <span class="sample-tag"> ... Sample</span>
   ```
4. Only publish reviews you have permission to use. Never invent reviews — beyond being dishonest, fabricated testimonials can breach Australian Consumer Law.

---

## 8. Update the team & founder bio

- **Founder bio:** open `team.html` and edit the paragraphs under "Meet Arun" to add or adjust detail. (Per your instruction, the site deliberately does **not** mention any current or past employer — keep it that way unless you decide otherwise.)
- **Add real team members:** the team page currently shows role-based capability cards ("Tax & compliance specialists", etc.) rather than invented people. When you're ready to add named staff, copy the founder card block in `team.html`, change the name, title and bio, and add a photo if you like. The website guide block on that page points to this section.
- **Add a founder photo:** put the image file (e.g. `arun.jpg`) in the website folder, then in `team.html` replace the diamond logo block at the top of the founder card with:
  ```html
  <img src="arun.jpg" alt="Arun Kalluparampil" style="width:96px;height:96px;border-radius:50%;object-fit:cover;margin:0 auto 18px">
  ```

---

## 9. How to edit the files (free tools)

- Download **Visual Studio Code** (free): **https://code.visualstudio.com**
- Open the **whole website folder**: *File → Open Folder*.
- To change text site-wide, use **Edit → Replace in Files** (magnifying-glass icon with the arrow). This is how you'll update the Web3Forms key, phone number or email everywhere at once.
- After editing, **save** and **re-upload** the folder to your host (on Netlify Drop, just drag the folder onto your site's "Deploys" tab again).

**Want to change colours or fonts?** Everything visual lives in `shared.css` at the very top, in the `:root` section — the brand blues, the gold accent, fonts and spacing are all defined there as easy-to-find variables.

---

## 10. The digital business card & QR code

- **Page:** `business-card.html`
- **What the QR does:** when someone scans it with their phone camera, the phone offers to **save Arun as a contact** — name, title, phone, email, address and website all pre-filled. No app needed.
- **Two layers of reliability:** the page regenerates the QR live in the browser, and also ships a backup image (`qr-arun.png`). The **"Download .vcf file"** and **"Save contact"** buttons let people save the contact directly even without scanning.
- **If your details change:** update them in the contact card and regenerate the `.vcf`/QR. If you're not comfortable doing that, just ask your developer — or get back in touch and it can be regenerated for you. The contact details are also stored in `arun-kalluparampil.vcf` (open it in any text editor to see the format).

---

## 11. Accessibility, themes & other built-in features

These all work automatically — nothing to configure:

- **Light / Dark theme** toggle (top bar). The visitor's choice is remembered on their device.
- **Accessibility panel** (the person icon): text-size control, grayscale, underline-all-links, and reduce-motion. Choices are remembered.
- **Back-to-top** button appears when scrolling.
- **Keyboard friendly:** a "Skip to content" link and visible focus outlines for keyboard users.
- **Mobile menu:** the hamburger icon on phones/tablets.
- **SEO basics:** every page has a title, description, social-share tags and structured data; `sitemap.xml` and `robots.txt` are included. After launch, you can submit your site to **Google Search Console** (free) to help it appear in search.

---

## 12. Pre-launch checklist

- [ ] Buy `tensquare.com.au` (needs your ABN).
- [ ] Publish the folder to Netlify / Cloudflare / GitHub (free).
- [ ] Connect your domain (the host gives you the exact DNS values).
- [ ] Sign up at web3forms.com and replace `YOUR_WEB3FORMS_ACCESS_KEY` in all files.
- [ ] Send yourself a test enquiry through the contact form.
- [ ] Replace sample testimonials as real ones come in; remove the "Sample" tag.
- [ ] Double-check the phone number, email and address on the Contact and Business Card pages.
- [ ] (Optional) Add a founder/team photo.
- [ ] (Optional) Submit your site to Google Search Console.

---

## 13. Costs at a glance

| Item | Cost |
|---|---|
| Domain (`.com.au`) | ~AUD $15–25 / year |
| Hosting (Netlify / Cloudflare / GitHub Pages) | **Free** |
| HTTPS / SSL padlock | **Free** (automatic) |
| Contact form (Web3Forms free tier) | **Free** |
| WhatsApp & email links | **Free** |
| **Typical total** | **~$20 / year** |

---

## 14. A few important notes

- **Placeholders to replace before going live:** `YOUR_WEB3FORMS_ACCESS_KEY` (in all HTML files). Everything else is real and ready.
- **Legal pages** (`privacy.html`, `terms.html`) are solid starting templates aligned with the Australian Privacy Act. Have them reviewed to be sure they match your exact practices.
- **Articles** are general information and include the appropriate "general advice" disclaimers. Edit freely or add new ones by copying an existing `post-*.html` file.
- **Honesty by design:** the site contains no fabricated statistics or reviews. Numbers like "5 service areas" are factual; testimonials are labelled samples until you supply real ones.

---

*Built for Tensquare Accounting & Tax — a CPA practice. Liability limited by a scheme approved under Professional Standards Legislation. ABN 20 772 623 135.*
