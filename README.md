[![Netlify Status](https://api.netlify.com/api/v1/badges/0cf4dff5-5e46-4800-b26d-5e6448668c5c/deploy-status)](https://app.netlify.com/projects/the-unhurried-lifestyle/deploys)

# The Unhurried Lifestyle

A calm, single-page static site for a holistic wellness brand.
**Tagline:** *Gentle habits for a calmer, healthier life.*

Plain HTML + CSS with a touch of vanilla JS — no frameworks, no build step.
`index.html` is self-contained; `netlify.toml` is zero-config; the `email/`
folder holds the ready-to-paste MailerLite welcome email.

---

## 1 · Deploy to Netlify

You can deploy in either of two ways. Both take a couple of minutes.

### Option A — Drag & drop (fastest)
1. Go to <https://app.netlify.com/drop>.
2. Drag the whole project folder (the one containing `index.html`) onto the page.
3. Netlify gives you a live URL instantly, e.g. `something-calm-1234.netlify.app`.

### Option B — Connect this Git repo (auto-deploys on every push)
1. In Netlify, click **Add new site → Import an existing project**.
2. Choose your Git provider and pick this repository.
3. Build settings — leave them empty:
   - **Build command:** *(blank)*
   - **Publish directory:** `.`
   These are already set in `netlify.toml`, so you can just click **Deploy**.
4. Every push to your branch now redeploys automatically.

---

## 2 · Connect your custom domain (theunhurried.lifestyle)

1. In your site, go to **Domain management → Add a domain**.
2. Enter `theunhurried.lifestyle` and confirm you own it.
3. Point the domain at Netlify. Two common paths:
   - **Easiest — use Netlify DNS:** Netlify shows you 4 name servers. Log in to
     your domain registrar (where you bought the domain) and replace the
     existing name servers with Netlify's. DNS can take a few hours to settle.
   - **Keep your current DNS:** add these records at your registrar instead:
     - `A` record for the apex `@` → `75.2.60.5`
     - `CNAME` record for `www` → `your-site-name.netlify.app`
4. Back in Netlify, click **Verify / Set up HTTPS**. Netlify provisions a free
   Let's Encrypt SSL certificate automatically once DNS resolves.

That's it — your site will be live at `https://theunhurried.lifestyle`.

---

## 3 · Where to paste your real links

Open `index.html` and search for **`SWAP THIS LINK`** — each spot is marked with
a comment. Replace `href="#"` with your real URL:

| Section | What to replace | Where |
| --- | --- | --- |
| **The Unhurried Reset** (product) | Your Gumroad / checkout URL | `<a class="btn btn-clay" href="#">Get it here</a>` |
| **My calm-living essentials** | Your affiliate URLs (4 items) | each `<a class="link" href="#">View →</a>` |

You can also edit the essentials' **titles and descriptions** to match the real
products you recommend.

---

## 4 · The free guide email form (MailerLite)

The signup form posts straight to **MailerLite**, which delivers the guide
automatically via an autoresponder — no backend, no server.

### One-time setup
1. **Create a MailerLite account** (free tier is plenty to start).
2. **Authenticate your domain** (MailerLite → Settings → Domains) so emails
   send from `hello@theunhurried.lifestyle` and land in inboxes, not spam.
3. **Create a Group** (e.g. *Free Guide*) and an **Embedded form** for it.
   Choose the **"HTML form" / build-your-own** option — that screen shows your
   **Account ID** and **Form ID**.
4. **Paste those two IDs** into the form's `action` in `index.html`. Search for
   `MAILERLITE_ACCOUNT_ID` and `MAILERLITE_FORM_ID` and replace both:
   ```
   action="https://assets.mailerlite.com/jsonp/MAILERLITE_ACCOUNT_ID/forms/MAILERLITE_FORM_ID/subscribe"
   ```
5. **Build the delivery automation** (this is what actually sends the guide):
   - **Trigger:** *Subscriber joins the "Free Guide" group*
   - **Action:** *Send email* → use the ready-made template in
     [`email/welcome-guide-email.html`](email/welcome-guide-email.html)
   - In that email, set the download button to your real PDF link, e.g.
     `https://theunhurried.lifestyle/5-unhurried-morning-habits.pdf`
     (drop the PDF into this repo so it deploys with the site).

After someone signs up they see a calm in-page thank-you, then MailerLite's
confirmation + welcome email delivers the guide. Done — hands-off.

> Prefer MailerLite's copy-paste **JavaScript snippet** instead? You can drop it
> in and delete the `<form>` in `index.html`. The custom form is included
> because it keeps the calm, on-brand styling and the in-page thank-you.

### Your welcome email
`email/welcome-guide-email.html` is a ready-to-paste, **email-safe** HTML
template (on-brand sage/clay, table-based, inline styles, tested-pattern markup
that survives Outlook). The matching **MJML source** is
`email/welcome-guide-email.mjml` if you'd rather edit in MJML and recompile.
See `email/README.md` for exactly what to swap in and how to paste it into
MailerLite.

---

## Editing notes

- **Colours & fonts** live in the `:root` block near the top of `index.html`'s
  `<style>` section — change them in one place.
- **Copy** is plain text in the HTML; edit freely.
- Everything is in one file, so it's easy to tweak and re-deploy.

Take your time. 🌿
