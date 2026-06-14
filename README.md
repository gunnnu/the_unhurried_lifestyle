# The Unhurried Lifestyle

A calm, single-page static site for a holistic wellness brand.
**Tagline:** *Gentle habits for a calmer, healthier life.*

Plain HTML + CSS with a touch of vanilla JS — no frameworks, no build step.
Just `index.html` (everything is self-contained), `netlify.toml`, and this README.

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

## 4 · The free guide email form

The signup form uses **Netlify Forms** — no backend, no external service needed.

- Submissions appear in your Netlify dashboard under **Forms → free-guide**.
- After someone submits, they see a calm in-page thank-you message.

**To actually deliver the PDF "5 Unhurried Morning Habits":**
1. Add your PDF to this project (e.g. `5-unhurried-morning-habits.pdf`) so it
   deploys with the site.
2. In **Netlify → Forms → Settings & notifications**, add a notification (or
   connect an automation like Zapier / Make) that emails new subscribers the
   download link: `https://theunhurried.lifestyle/5-unhurried-morning-habits.pdf`.

Prefer an email tool instead (ConvertKit, MailerLite, Beehiiv)? Replace the
`<form>` in `index.html` with that provider's embed code — the rest of the page
stays the same.

---

## Editing notes

- **Colours & fonts** live in the `:root` block near the top of `index.html`'s
  `<style>` section — change them in one place.
- **Copy** is plain text in the HTML; edit freely.
- Everything is in one file, so it's easy to tweak and re-deploy.

Take your time. 🌿
