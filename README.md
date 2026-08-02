# Constante Dizon II — Portfolio

A single-page portfolio site (dark navy/blue theme) highlighting the Filmetrics Odoo internship and the Paysafe LSTM-SVM thesis.

## Files
- `index.html` — the entire site (HTML/CSS/JS, no build step needed)
- `Dizon_Resume.pdf` — resume, linked from the Resume section

## Deploy to Vercel (2 minutes, no CLI needed)

1. Go to https://vercel.com and sign in (GitHub, GitLab, or email).
2. Click **Add New → Project**.
3. Choose **"Upload"** (or drag-and-drop) instead of importing a Git repo, and drop this whole folder in.
   - Alternative: push this folder to a new GitHub repo, then "Import" that repo in Vercel — this also gives you auto-deploys on every future push.
4. Framework preset: choose **"Other"** (it's a static site — no framework needed).
5. Click **Deploy**. Vercel will give you a live URL like `constante-portfolio.vercel.app` in under a minute.

## Deploy with the Vercel CLI (alternative)

```bash
npm i -g vercel
cd portfolio
vercel
```
Follow the prompts — it will detect this as a static site automatically.

## Customizing later
- Swap the "CD" initials circle in the hero for a real photo: replace the `.photo-inner` div content in `index.html` with an `<img>` tag.
- Update social links (LinkedIn/GitHub) in the hero `.socials` block.
- The contact form currently opens the visitor's email client (`mailto:`) since there's no backend — wire it to a service like Formspree or Vercel's own serverless functions if you want submissions to land somewhere without opening email.

## Wiring up the contact form to actually send email (free, no third-party form service)

The contact form now submits to your own serverless function — `api/contact.js` — which sends the email itself via Gmail's SMTP. This runs free on Vercel's Hobby plan; no Formspree account, no "allowed domains" quirks, and no branding but your own.

**Setup (one-time, ~5 minutes):**

1. **Turn on 2-Step Verification** on the Gmail account you want to send from (`dizonconstante3@gmail.com`), if it isn't already: https://myaccount.google.com/security
2. **Generate an App Password**: https://myaccount.google.com/apppasswords → choose "Mail" as the app → copy the 16-character password it gives you (spaces don't matter).
3. In your **Vercel project dashboard** → Settings → Environment Variables, add two variables:
   - `GMAIL_USER` = `dizonconstante3@gmail.com`
   - `GMAIL_APP_PASSWORD` = the 16-character App Password from step 2 (not your normal Gmail password)
4. Redeploy the project (Vercel → Deployments → Redeploy, or just push again) so the new env vars take effect.
5. Test the form on your **live Vercel URL**. It won't work with plain Live Server locally since that doesn't run serverless functions — use `vercel dev` if you want to test locally, or just test on the deployed site.

That's it — every submission emails `dizonconstante3@gmail.com` directly, with the sender's address set as reply-to so you can just hit "Reply" in Gmail.

### Files this added
- `api/contact.js` — the serverless function (Node.js + Nodemailer)
- `package.json` — declares the `nodemailer` dependency so Vercel installs it automatically during deploy

