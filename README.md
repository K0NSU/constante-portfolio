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
