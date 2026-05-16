# Sales-Page Deployment Guide

Step-by-step for getting these HTML pages live and Digistore24-approved.

## What's in this folder

```
salespage/
├── index.html                       — Landing page (both products)
├── repair-script/index.html         — Sales page for The 12-Minute Repair Script
├── notice-name-reset/index.html     — Sales page for Notice · Name · Reset
├── imprint/index.html               — Legal imprint (REQUIRED by D24)
├── privacy/index.html               — Privacy policy
├── terms/index.html                 — Terms of service incl. refund policy
├── thank-you/index.html             — Post-purchase page (REQUIRED by D24)
└── assets/
    ├── styles.css                   — Shared stylesheet
    ├── cover_repair_400x520.png/jpg
    ├── cover_calm_400x520.png/jpg
    ├── logo_ao_team_640x500.jpg
    └── lookinside_*.png             — 6 carousel images
```

All HTML pages are **standalone static files** — no build step, no JavaScript framework, no server needed. Just upload and they work.

---

## STEP 1 — Fill in the 2 remaining placeholders (5 minutes)

All branding, address, name, and phone are already baked in. Two placeholders still need filling — find-and-replace across all files.

| Placeholder | What to replace it with | Where it appears |
|---|---|---|
| `[REPLACE_ME_CONTACT_EMAIL]` | A monitored support email (e.g. `support@calmconnectedguides.com` or any working email you control) | imprint, privacy, terms, thank-you, repair-script, notice-name-reset, index |
| `[REPLACE_ME_DIGISTORE24_ORDER_URL]` | The buy-button URL D24 issues AFTER your product is approved. **Leave the placeholder for first deploy**; replace once D24 gives you the URL | `repair-script/index.html` and `notice-name-reset/index.html` |

Already filled in (no action needed):
- Provider: Muzzammil Sarwar (sole proprietor), trading as Calm & Connected Guides
- Address: House 639, Street 44, G-9/1, Islamabad 44000, Pakistan
- Phone: +92 335 9348075

**Quick way on Windows:**
- Open the `salespage` folder in VS Code (free)
- Press `Ctrl + Shift + H` (find-and-replace across files)
- Enter the placeholder, enter the real value, click "Replace All"
- Repeat for each placeholder

**The D24 order URL won't exist yet** when you first deploy. That's OK — deploy with the placeholder, submit the product to D24 for approval. D24 will give you the order URL during approval. Then come back and replace.

---

## STEP 2 — Deploy to GitHub Pages (your chosen path)

GitHub Pages serves static HTML for free from any public repo. Steps:

### 2a — Create the repo

1. Sign in to **[github.com](https://github.com)** (or sign up — free)
2. Click the **+ icon** top-right → **New repository**
3. Repository name: `calm-connected-guides` (becomes part of the URL)
4. Visibility: **Public** (GitHub Pages on free plan requires public repos)
5. **Don't** initialise with a README, .gitignore, or licence — keep it empty
6. Click **Create repository**

### 2b — Upload the files (no Git CLI needed)

On the empty repo page, click **"uploading an existing file"** (the link in the middle of the screen).

1. Open the `salespage` folder in File Explorer
2. **Select everything INSIDE the `salespage` folder** (not the folder itself — the contents):
   - `index.html`
   - `repair-script/` folder
   - `notice-name-reset/` folder
   - `imprint/` folder
   - `privacy/` folder
   - `terms/` folder
   - `thank-you/` folder
   - `assets/` folder
   - (you can skip `DEPLOYMENT.md` — that's for you, not for the public site)
3. Drag them into the GitHub upload area
4. Wait for all files to upload (~30 seconds — there are ~20 files including images)
5. At the bottom, **commit message:** "Initial site"
6. Click **Commit changes**

### 2c — Enable GitHub Pages

1. In the repo, go to **Settings** (top right tab) → **Pages** (left sidebar)
2. Under **Source**, select **Deploy from a branch**
3. Branch: **main**, folder: **/ (root)**
4. Click **Save**
5. Wait 1–2 minutes — GitHub builds the site
6. Refresh the Pages settings; you'll see "Your site is live at `https://[your-username].github.io/calm-connected-guides/`"

### 2d — Verify the pages work

Open these in a browser (replace `[your-username]` with your GitHub username):
- `https://[your-username].github.io/calm-connected-guides/` (landing)
- `https://[your-username].github.io/calm-connected-guides/repair-script/`
- `https://[your-username].github.io/calm-connected-guides/notice-name-reset/`
- `https://[your-username].github.io/calm-connected-guides/imprint/`
- `https://[your-username].github.io/calm-connected-guides/privacy/`
- `https://[your-username].github.io/calm-connected-guides/terms/`
- `https://[your-username].github.io/calm-connected-guides/thank-you/`

If images don't load, double-check that the `assets/` folder uploaded with all 11 files inside.

### 2e — Custom domain (optional)

If you own a domain (e.g. `calmconnectedguides.com`):
1. In the repo: **Settings → Pages → Custom domain** → enter your domain → Save
2. At your domain registrar, add a CNAME record:
   - Name: `@` (or `guides` for a subdomain)
   - Value: `[your-username].github.io`
3. Wait 10–30 minutes for HTTPS to provision
4. Tick **"Enforce HTTPS"** in the Pages settings

If you don't own a domain, the free `*.github.io` URL is **fine for D24** — they accept it.

### Alternative — Cloudflare Pages (faster CDN, drag-and-drop, no Git knowledge)

If GitHub gives you trouble, the same files deploy on Cloudflare Pages in 5 minutes:
1. Sign up at **[dash.cloudflare.com/sign-up](https://dash.cloudflare.com/sign-up)**
2. **Workers & Pages → Create application → Pages → Upload assets**
3. Name the project, drag the `salespage` folder, click Deploy
4. Live at `https://[project-name].pages.dev` in ~30 seconds

---

## STEP 3 — Update Digistore24 product settings (5 minutes)

Once the pages are live, go back to your D24 vendor dashboard for each product:

1. **My products** → click the product
2. **Sales page URL** → paste the full URL:
   - For the Repair Script product: `https://aoteam-guides.pages.dev/repair-script/`
   - For the Calm Guide product: `https://aoteam-guides.pages.dev/notice-name-reset/`
3. **Thank-you page URL** → paste: `https://aoteam-guides.pages.dev/thank-you/`
4. **Return policy** → set to **60 days** (matches what's stated on the sales page)
5. **Submit for review**

---

## STEP 4 — Pre-submission self-check (use D24's checklist)

Before clicking "Submit", verify every item from D24's checklist screen:

- [ ] **You have made a test purchase via the buy button.** D24 lets vendors use a test card / promo code — check their "Test purchase" docs. You're verifying that clicking the button on the sales page actually reaches D24 checkout.
- [ ] **The sales page contains no links leading to another payment process outside of Digistore24.** Confirmed — the only "buy" link is the `[REPLACE_ME_DIGISTORE24_ORDER_URL]` you'll paste in.
- [ ] **The sales page is freely accessible and not password-protected.** Cloudflare Pages is public by default. Open the URL in an incognito window to double-check.
- [ ] **The purchasable product is described completely.** Both sales pages have: title, deliverable (11-page or 10-page PDF), price ($12), what's inside, look-inside images, FAQ. ✓
- [ ] **The return policy matches the product settings.** Both pages state 60-day refund. Set product settings to 60 days. ✓
- [ ] **Imprint is visible from every page.** Footer link on every page → imprint/index.html. ✓
- [ ] **Privacy + Terms are linked from the sales page.** Footer links. ✓

---

## STEP 5 — Submit for review

D24 reviews on weekdays. Expected timeline:
- **24 hours** if the page meets all requirements first time
- **Up to 48 hours** if they request one revision (they give you a 48-hour fix window)

Common reasons they reject (avoid these):
- Refund period on the page doesn't match product settings → already aligned
- Missing imprint → already included
- Vague deliverable description → already states "11-page PDF, instant download"
- Medical/therapeutic claims → the calm guide carefully avoids these (we say "support daily stress and mindfulness practice", not "treat anxiety")
- Broken thank-you page → already included

---

## Backup option — GitHub Pages

If for some reason Cloudflare Pages doesn't work for you:

1. Create a GitHub account (free)
2. Create a new public repo called `aoteam-guides`
3. From the repo page → **Add file → Upload files** → drag the contents of `salespage/` (not the folder itself, the contents) → commit
4. **Settings → Pages** → Source: **Deploy from a branch** → branch `main`, folder `/` (root) → Save
5. Wait 1–2 minutes
6. Your site is live at `https://[your-github-username].github.io/aoteam-guides/`

Caveat: GitHub Pages URLs are uglier than Cloudflare's, and the paths in this repo use clean directory URLs (e.g. `/repair-script/`) which work the same way on GitHub Pages — but you might want to verify by testing.

---

## Backup option — your existing Hostinger VPS

If you'd rather host on your existing Hostinger VPS (per the memory note about your Time Tracker MVP):

1. SSH into your VPS
2. Copy the `salespage/` folder via `scp` or `rsync`:
   ```bash
   rsync -avz ./salespage/ user@your-vps:/var/www/aoteam-guides/
   ```
3. Configure Nginx to serve it as a static site at a subdomain (e.g. `guides.aoteam.com`):
   ```nginx
   server {
       listen 80;
       server_name guides.aoteam.com;
       root /var/www/aoteam-guides;
       index index.html;
       location / {
           try_files $uri $uri/ $uri/index.html =404;
       }
   }
   ```
4. Point a DNS A record `guides.aoteam.com → your VPS IP`
5. Run `certbot --nginx -d guides.aoteam.com` for free HTTPS

This works fine, but adds maintenance overhead vs. Cloudflare Pages. **Use Cloudflare Pages unless you want everything on your VPS for centralization.**

---

## Updating the pages later

If you want to edit copy, change a price, or update the imprint:

**Cloudflare Pages:**
- Edit the HTML files locally
- Go to your project → **Create deployment** → drag the updated folder
- Live in ~30 seconds

**GitHub Pages:**
- Commit changes to the repo
- Auto-deploys within 1–2 minutes

---

## Quick sanity check

Right now, after replacing placeholders and deploying, your URLs should be:

```
Sales page 1:   https://[your-domain]/repair-script/
Sales page 2:   https://[your-domain]/notice-name-reset/
Thank you:      https://[your-domain]/thank-you/
Imprint:        https://[your-domain]/imprint/
Privacy:        https://[your-domain]/privacy/
Terms:          https://[your-domain]/terms/
```

That's everything D24 asks for. Submit and you should be approved within 24h.
