# Welcome / freebie email

The email MailerLite sends automatically when someone signs up for the free
guide. It's on-brand (sage / clay / Fraunces) and **email-safe** — table-based
layout with inline styles, so it holds up across Outlook, Gmail, Apple Mail, etc.

| File | What it is |
| --- | --- |
| `welcome-guide-email.html` | **Paste-ready.** The compiled, email-safe HTML to drop into MailerLite. |
| `welcome-guide-email.mjml` | The MJML source — edit here if you want to make changes, then recompile. |

## Swap these two things before sending

Open `welcome-guide-email.html` and replace:

1. **`LOGO_URL`** → a publicly hosted logo, e.g.
   `https://theunhurried.lifestyle/assets/images/the_unhurried_lifestyle_no_bg.png`
   (Email can't use a local file — it must be a full `https://` URL. Your logo
   already deploys with the site, so just point at it.)
2. **`PDF_DOWNLOAD_URL`** → your real guide link, e.g.
   `https://theunhurried.lifestyle/5-unhurried-morning-habits.pdf`
   (Drop the PDF into the repo root so it deploys with the site.)

> The `{$unsubscribe}` and `{$account.*}` tags are MailerLite merge tags — it
> fills them in automatically. Leave them as-is (they're required for
> legitimate, CAN-SPAM-compliant email).

## Paste it into MailerLite

1. MailerLite → **Automations** → create one.
2. **Trigger:** *Subscriber joins a group* → your *Free Guide* group.
3. **Action:** *Email* → in the email editor pick the **"Custom HTML"** editor.
4. Paste the full contents of `welcome-guide-email.html`.
5. Send yourself a **test** (always test before going live), then turn the
   automation on.

## Editing later (optional)

Prefer to tweak copy or layout in MJML? Edit `welcome-guide-email.mjml`, then:

```bash
npx mjml email/welcome-guide-email.mjml -o email/welcome-guide-email.html
```

…and re-paste the regenerated HTML. Or use the live editor at
<https://mjml.io/try-it-live>.
