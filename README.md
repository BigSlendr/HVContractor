# Heartland Village General Contracting & Handyman Services
## Static Website — GitHub Pages / Cloudflare Pages

---

### 🚀 Deploy in 3 Steps

**GitHub Pages:**
1. Create a new GitHub repo (e.g. `heartland-village-site`)
2. Upload all files maintaining this folder structure
3. Go to Settings → Pages → Source: `main` branch → `/root`
4. Live at: `https://yourusername.github.io/heartland-village-site/`

**Cloudflare Pages (recommended — faster + free custom domain):**
1. Push repo to GitHub
2. Cloudflare Dashboard → Pages → Connect to Git → Select repo
3. Build settings: Framework = None, Build command = (leave blank), Output = `/`
4. Connect custom domain in Cloudflare DNS

---

### 📋 Before Going Live — Checklist

- [ ] Replace Formspree ID: In `index.html`, find `https://formspree.io/f/YOUR_FORM_ID` and replace with your real Formspree endpoint (free at formspree.io)
- [ ] Add project photos to `/assets/` and update gallery section
- [ ] Verify phone number: (347) 256-4940
- [ ] Test contact form submission
- [ ] Test mobile nav on phone

---

### 🔄 Monthly Maintenance (Reviews + Photos)

**Adding a new review:**
Open `index.html` → find `reviews-grid` section → paste this block:

```html
<div class="review-card">
  <div class="review-stars">★★★★★</div>
  <p class="review-text">"Review text here."</p>
  <div class="review-meta">
    <strong>Customer Name</strong>
    <span>Staten Island · Month Year</span>
    <div class="review-source">via Angi</div>
  </div>
</div>
```

**Adding a project photo:**
1. Add image file to `/assets/` folder
2. In `index.html`, find `gallery-grid` section
3. Replace a placeholder with: `<div class="gallery-item"><img src="assets/filename.jpg" alt="Description" /></div>`
4. Use `gallery-item--wide` class for landscape/wide photos

---

### 📁 File Structure

```
/
├── index.html          ← Main page (all sections)
├── css/
│   └── styles.css      ← All styles
├── js/
│   └── main.js         ← Nav, animations, form handling
├── assets/             ← Project photos go here
│   └── (photos)
└── README.md
```

---

### 📞 Business Info
- **Phone:** (347) 256-4940
- **Hours:** 24/7 including emergencies
- **Service Area:** Staten Island, Nassau County, New Jersey
- **Angi Profile:** https://www.angi.com/companylist/us/ny/staten-island/heartland-village-general-contracting-and-handyman-services-reviews-9113959.htm
