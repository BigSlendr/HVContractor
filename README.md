# Heartland Village General Contracting & Handyman Services
### Website — Static HTML · Tailwind CSS · GitHub Pages

**Live site:** _add your URL here once deployed_
**Phone:** (347) 256-4940 · **Hours:** Open 24/7 · **Service Area:** Staten Island · Nassau County · New Jersey

---

## Table of Contents

1. [Overview](#overview)
2. [File Structure](#file-structure)
3. [First-Time Setup & Deployment](#first-time-setup--deployment)
4. [Connecting a Custom Domain](#connecting-a-custom-domain)
5. [Monthly Maintenance — Reviews](#monthly-maintenance--reviews)
6. [Monthly Maintenance — Gallery Photos](#monthly-maintenance--gallery-photos)
7. [Making Other Edits](#making-other-edits)
8. [Business Info Reference](#business-info-reference)

---

## Overview

This is a static website — plain HTML files styled with Tailwind CSS. There is no build step, no Node.js, no React, and no server required. Every page is a standalone `.html` file that can be opened in a browser directly.

The site consists of 5 pages:

| Page | File | Purpose |
|------|------|---------|
| Home | `index.html` | Hero, services preview, reviews preview, CTA |
| Services | `services.html` | Full list of all services offered |
| Reviews | `reviews.html` | All customer reviews — **updated monthly** |
| Gallery | `gallery.html` | Project photos with category filters — **updated monthly** |
| Contact | `contact.html` | Phone number, hours, service area, credentials |

Deployment is fully automated via GitHub Actions — every push to the `main` branch republishes the site within about 60 seconds.

---

## File Structure

```
/
├── index.html              ← Homepage
├── services.html           ← Services page
├── reviews.html            ← Reviews page (update monthly)
├── gallery.html            ← Gallery page (update monthly)
├── contact.html            ← Contact page
├── styles.css              ← All shared styles (nav, cards, mobile bar, etc.)
├── README.md               ← This file
├── .gitignore
├── img/
│   ├── hero.jpg            ← Hero background photo (replace with real project photo)
│   └── [project photos]    ← All gallery images live here, flat (no subfolders needed)
└── .github/
    └── workflows/
        └── deploy.yml      ← GitHub Actions — auto-deploys on push to main
```

> **Image naming convention:** Name photos descriptively so they're easy to manage.
> Examples: `deck-build-april-2025.jpg`, `kitchen-remodel-march-2025.jpg`, `bathroom-tile-2025.jpg`

---

## First-Time Setup & Deployment

### Step 1 — Create the GitHub Repository

1. Go to [github.com](https://github.com) and sign in
2. Click **New repository**
3. Name it: `heartland-village-site` (or anything you prefer)
4. Set to **Public**
5. Do **not** initialize with a README (you already have one)
6. Click **Create repository**

### Step 2 — Upload the Files

**Option A — GitHub web UI (no terminal needed):**
1. On the new repo page, click **uploading an existing file**
2. Drag and drop ALL files from the zip — including the `img/` folder, `.github/` folder, and `styles.css`
3. Scroll down, write a commit message like `Initial site upload`
4. Click **Commit changes**

**Option B — Git CLI:**
```bash
git init
git remote add origin https://github.com/YOURUSERNAME/heartland-village-site.git
git add .
git commit -m "Initial site upload"
git branch -M main
git push -u origin main
```

### Step 3 — Enable GitHub Pages

1. In your repo, go to **Settings** → **Pages** (left sidebar)
2. Under **Source**, select **GitHub Actions**
3. That's it — the `deploy.yml` workflow handles everything automatically

### Step 4 — Confirm Deployment

1. Click the **Actions** tab in your repo
2. You should see a workflow run called `Deploy to GitHub Pages`
3. Once it shows a green checkmark, your site is live
4. Your URL will be: `https://YOURUSERNAME.github.io/heartland-village-site/`

> First deployment typically takes 1–2 minutes. Subsequent pushes deploy in about 60 seconds.

---

## Connecting a Custom Domain

If you have a domain (e.g. `heartlandvillageny.com`):

### Step 1 — Add a CNAME file to the repo

Create a file called `CNAME` (no extension) in the root of the repo containing just your domain:

```
heartlandvillageny.com
```

Commit and push it.

### Step 2 — Update your DNS

Log into your domain registrar (GoDaddy, Namecheap, Google Domains, etc.) and add these DNS records:

| Type | Host | Value |
|------|------|-------|
| A | @ | 185.199.108.153 |
| A | @ | 185.199.109.153 |
| A | @ | 185.199.110.153 |
| A | @ | 185.199.111.153 |
| CNAME | www | YOURUSERNAME.github.io |

### Step 3 — Enable HTTPS in GitHub

1. Go to **Settings → Pages**
2. Under **Custom domain**, enter your domain and click Save
3. Check **Enforce HTTPS** once it becomes available (usually within 24 hours)

> DNS propagation can take up to 48 hours, though it usually resolves within a few hours.

---

## Monthly Maintenance — Reviews

Check Angi and HomeAdvisor monthly for new 4★ and 5★ reviews. Only add reviews with 4 or 5 stars.

### How to add a new review

1. Open `reviews.html` in GitHub (click the file → click the pencil ✏️ icon to edit)
2. Find this comment near the top of the reviews grid:
   ```html
   <!-- ADD NEW REVIEWS AT THE TOP — newest first -->
   ```
3. Paste the following block **directly below that comment**:

```html
<article class="card reveal">
  <p class="stars mb-2">★★★★★</p>
  <h3>REVIEWER NAME</h3>
  <p class="text-xs text-gray-400 mb-3 font-semibold uppercase tracking-wide">
    Staten Island · MONTH YEAR · via Angi
  </p>
  <p>"PASTE THE REVIEW TEXT HERE"</p>
</article>
```

4. Replace the placeholder text with the real reviewer name, date, source (Angi / HomeAdvisor / Houzz), and review text
5. For a 4-star review, change `★★★★★` to `★★★★☆`
6. Scroll down, write a commit message like `Add review — Sue M. September 2025`
7. Click **Commit changes** — the site redeploys automatically within 60 seconds

### Example of a completed review block

```html
<article class="card reveal">
  <p class="stars mb-2">★★★★★</p>
  <h3>John D.</h3>
  <p class="text-xs text-gray-400 mb-3 font-semibold uppercase tracking-wide">
    Staten Island · April 2025 · via Angi
  </p>
  <p>"Harvey and his team did an incredible job on our deck. On time, on budget, and the craftsmanship was excellent. Would absolutely hire again."</p>
</article>
```

---

## Monthly Maintenance — Gallery Photos

### Step 1 — Upload the photo

1. In the GitHub repo, click on the `img/` folder
2. Click **Add file → Upload files**
3. Drag in your photo(s)
4. Name them clearly: `deck-april-2025.jpg`, `kitchen-remodel-2025.jpg`, etc.
5. Commit the upload

### Step 2 — Add the photo to the gallery page

1. Open `gallery.html` → click the pencil ✏️ icon to edit
2. Find this comment:
   ```html
   <!-- ADD NEW PHOTOS AT THE TOP — newest first -->
   ```
3. Paste this block **directly below that comment**:

```html
<div class="gallery-item" data-cat="CATEGORY">
  <div class="relative group cursor-pointer rounded-xl overflow-hidden"
       onclick="openLightbox('img/YOUR-PHOTO-FILENAME.jpg', 'Project Label')">
    <img src="img/YOUR-PHOTO-FILENAME.jpg"
         alt="Brief description of the project"
         loading="lazy"
         class="w-full object-cover" />
    <div class="absolute inset-0 bg-brand-navy/0 group-hover:bg-brand-navy/40 transition-colors flex items-end p-3 opacity-0 group-hover:opacity-100">
      <span class="text-white font-headline font-bold text-sm uppercase tracking-wide">Project Label</span>
    </div>
  </div>
</div>
```

4. Replace the placeholders:
   - `CATEGORY` → one of: `deck` · `flooring` · `kitchen` · `bathroom` · `exterior` · `restoration` · `ramp`
   - `YOUR-PHOTO-FILENAME.jpg` → exact filename you uploaded (case-sensitive)
   - `Project Label` → short label shown on hover, e.g. `Deck Build · Staten Island`
   - `alt="..."` → brief description for accessibility, e.g. `Deck construction with TREX railing`

5. Commit changes — site redeploys in ~60 seconds

### Example of a completed gallery block

```html
<div class="gallery-item" data-cat="deck">
  <div class="relative group cursor-pointer rounded-xl overflow-hidden"
       onclick="openLightbox('img/deck-april-2025.jpg', 'Deck Build · Staten Island')">
    <img src="img/deck-april-2025.jpg"
         alt="New TREX deck with metal railings, Staten Island"
         loading="lazy"
         class="w-full object-cover" />
    <div class="absolute inset-0 bg-brand-navy/0 group-hover:bg-brand-navy/40 transition-colors flex items-end p-3 opacity-0 group-hover:opacity-100">
      <span class="text-white font-headline font-bold text-sm uppercase tracking-wide">Deck Build · Staten Island</span>
    </div>
  </div>
</div>
```

### Hero background photo (one-time)

The hero on the homepage uses `img/hero.jpg`. Replace the placeholder with any real project photo — a finished deck, an exterior shot, or a before/after. Landscape orientation works best (wider than tall). Recommended minimum size: 1400px wide.

---

## Making Other Edits

All edits can be made directly in GitHub's web editor (click any file → pencil icon). No code editor or terminal required.

### Update the phone number
Search all files for `(347) 256-4940` and `+13472564940` — replace both formats everywhere they appear.

### Update the service area
Search for `Staten Island · Nassau County · New Jersey` and update as needed.

### Change the brand colors
Open `styles.css`. The color tokens are defined as CSS variables and as Tailwind config at the top of each HTML file:
- `brand-navy`: `#0d1b2a` — dark navy used for header, footer, hero, dark sections
- `brand-amber`: `#d4891a` — amber/gold used for accents, buttons, stars, highlights

### Add a new service
Open `services.html` → find the services grid → copy an existing `<article class="card">` block and edit the title and description.

---

## Business Info Reference

| Field | Value |
|-------|-------|
| Business Name | Heartland Village General Contracting & Handyman Services |
| Owner | Harvey |
| Phone | (347) 256-4940 |
| Hours | Open 24 Hours · 7 Days a Week |
| Emergency | Available 24/7 |
| Service Area | Staten Island · Nassau County · New Jersey |
| Founded | 1994 |
| Angi Rating | 4.8★ |
| Angi Awards | Super Service Award 2016–2025 (10 consecutive years) |
| Licenses | NY · NJ · Nassau County General Contractor |
| Certifications | EPA Lead Certified |
| Insurance | Fully Insured |
| Angi Profile | https://www.angi.com/companylist/us/ny/staten-island/heartland-village-general-contracting-and-handyman-services-reviews-9113959.htm |
