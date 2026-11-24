# API Portfolio Review

A single-page client review of the API portfolio, prepared by Driven Asset Management.
Static site: one HTML file, no build step, no server code, no database.

Position as at **11 November 2026** — 1,626 units, 87.8% occupied, AED 190.24M a year.

---

## What is in this repository

| File | Purpose |
|---|---|
| `index.html` | The whole review: markup, styles, data and animation in one file |
| `vercel.json` | Security headers, no-index rule and caching |
| `robots.txt` | Keeps the page out of search engines |
| `package.json` | Only a `dev` script for previewing locally |
| `.gitignore` | Keeps master sheets and local files out of the repository |

Nothing to install. The only external request is the Lato font from Google Fonts.

---

## Deploying

### 1. Put it on GitHub

```bash
git init
git add .
git commit -m "API portfolio review"
git branch -M main
git remote add origin https://github.com/<your-account>/api-portfolio.git
git push -u origin main
```

Make the repository **private**. It contains tenant names and rents.

### 2. Connect it to Vercel

1. Sign in at vercel.com and choose **Add New → Project**.
2. Import the repository.
3. Framework preset **Other**. Leave the build command and output directory empty.
4. Press **Deploy**. It takes about twenty seconds.

For your own address, go to **Settings → Domains** and add, for example,
`api-review.drivenproperties.com`, then create the CNAME record Vercel shows you.

### 3. Lock it down before sharing

- **Vercel Authentication** (Settings → Deployment Protection) limits the site to
  your Vercel team. Free on all plans.
- **Password Protection** (same screen, Pro plan) gives you one password to share
  with the client.

`vercel.json` already sends `X-Robots-Tag: noindex` and `robots.txt` disallows
crawling, so the page will not appear in search results either way.

---

## Updating the figures

The data sits inside `index.html`, in the `const D = {...}` line near the bottom.
Send the new API master sheet, replace the file and push:

```bash
git add index.html
git commit -m "Position as at <date>"
git push
```

Vercel redeploys within a minute, and every push keeps its own URL, so you can
always go back to the version a client was shown.

---

## Notes

- The villas API leases to Driven Properties appear once, as API’s own lease.
  Driven’s sub-let of those villas is not part of this review.

- Tested on phone, tablet, laptop and a 2560-wide screen; no horizontal scrolling.
- All animation respects the operating system's "reduce motion" setting.
- Blocked and legal units are counted in the portfolio but kept out of the
  occupancy rate, which matches the main dashboard.
