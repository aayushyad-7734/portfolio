# Portfolio Project Checkpoint
_Updated: 2026-03-22_

---

## Project Overview
Personal portfolio website for **Aayush Yadav** (Product & Business Analyst, IIT Delhi grad, ex-national squash player).

**Local file:** `/Users/aayushyadav/Downloads/final_portfolio/index.html`
**GitHub repo:** `https://github.com/aayushyad-7734/portfolio`
**Live URL:** `https://aayushyad-7734.github.io/portfolio/`
**Single file:** Everything (HTML + CSS + JS) is in `index.html`

---

## Tech Stack
- HTML, CSS, JavaScript (no frameworks, no backend)
- Hosted on GitHub Pages (free static hosting)
- GitHub CLI (`gh`) authenticated via personal access token

---

## Design
- **Theme:** Dark background (`#0a0a0a`), light pink accent (`#e8a0b4`), off-white text (`#f0ece6`)
- **Fonts:** Instrument Serif (headings), DM Sans (body), JetBrains Mono (labels/tags)
- **Features:** Custom pink cursor dot (desktop only), scroll-reveal animations, frosted glass nav

---

## Nav Structure
Fixed top nav with:
- Logo: `aayush.` (left)
- Tabs: About · Experience · Projects · Skills · Recognition · Gallery (center)
- **Connect button:** Outlined pink border, scrolls to contact section
- **Resume button:** Filled pink, opens resume modal
- **Mobile:** Hamburger menu toggles tabs + Connect/Resume buttons

---

## Page Sections (in order)
1. **Hero** — Photo (`image.jpg`), name, title, tagline
2. **About** (`#about`) — Bio, 3 key stats, detail cards (Education, Current Role, Athletics)
3. **Experience** (`#experience`) — Timeline with Policybazaar roles
4. **Projects** (`#projects`) — 2×2 grid, each card opens a modal via "View More →"
5. **Skills** (`#skills`) — Pill tags
6. **Recognition** (`#awards`) — 4 award items + photo carousel (`#gallery`)
7. **Contact** (`#contact`) — "Let's build something great" + email/LinkedIn/phone

---

## Project Modals
Each project card opens a modal with: Overview, Design Approach, Tools & Stack, Impact.

### Modal content:
- **PROJECT 01 — Mindlessly:** Chrome extension. "How It Works" section with 3 screenshots. Click screenshot → lightbox with Back button + prev/next arrows + counter.
- **PROJECT 02 — AI Sales Coach:** NotebookLM + transcription API. "Output Preview" with `call-score.jpg`.
- **PROJECT 03 — Data Intelligence KB:** Custom GPT + SQL knowledge base.
- **PROJECT 04 — Social Proof MVP:** Claude Code + pincode customer density.

---

## Lightbox Features
- **← Back button** (top-left) — closes lightbox, returns to modal
- **‹ / › arrows** — navigate between flow screenshots (Mindlessly has 3)
- **1 / 3 counter** (bottom-center) — shows current position
- **Arrow keys** — Left/Right navigate, Escape closes
- Single-image lightboxes (like AI Sales Coach) hide arrows/counter

---

## Photo Gallery
- Horizontal auto-scrolling carousel with blur/focus effect
- 11 images in `medals/` subfolder
- Auto-scrolls every 2.8s, pauses on interaction
- Wheel scroll to navigate, click to focus, click focused → lightbox

---

## Resume Modal
- Opens PDF in iframe, lazy-loads on open
- Download button inside modal
- File: `resume.pdf`

---

## Safari Scroll Fix (Root Cause & Solution)

### Root Cause
The `resumeModal` element (`position: fixed; z-index: 1101; display: flex; opacity: 0; pointer-events: none`) was blocking scroll events in Safari/WebKit. Even though invisible, WebKit still routes scroll/wheel events to the topmost fixed-position element in the rendering tree. The hidden resume modal was silently consuming scroll events meant for the project modal below it.

### Solution
Added `visibility: hidden` to ALL inactive overlay elements (modals, backdrops, lightbox). Unlike `opacity: 0` + `pointer-events: none`, `visibility: hidden` fully removes elements from WebKit's scroll event routing.

### Other CSS changes made:
- Replaced `transform: translate(-50%, -50%)` centering with `inset: 0; margin: auto` (avoids Safari transform+scroll bug)
- Added `height: fit-content` to `.modal`
- Added `::-webkit-scrollbar` pseudo-elements (Safari doesn't support `scrollbar-width`/`scrollbar-color`)
- Body scroll lock uses `position: fixed` technique (preserves/restores scroll position)

---

## Mobile Responsive
- Hamburger menu with working toggle (tabs + Connect/Resume appear in dropdown)
- Menu closes on nav link click
- Single-column layouts for projects, about grid
- Modal sized to 96vw, adjusted padding
- Lightbox controls sized down
- Cursor dot hidden on mobile
- Hero photo margin removed on mobile

---

## Asset Files
```
index.html              ← main file (was portfolio.html, renamed for GitHub Pages)
image.jpg               ← hero profile photo
resume.pdf              ← CV
call-score.jpg          ← AI Sales Coach output preview
mindlessly-1.jpg        ← Step 1 screenshot
mindlessly-2.jpg        ← Step 2 screenshot
mindlessly-3.jpg        ← Step 3 screenshot
Portfolio_photo.png     ← alternate photo
CHECKPOINT.md           ← this file
medals/                 ← 11 trophy/medal photos for gallery
```

---

## Person Info
- **Name:** Aayush Yadav
- **Email:** yadaayush7734@gmail.com
- **Phone:** +91-7734023243
- **LinkedIn:** linkedin.com/in/aayush-yadav-38a880229
- **College:** IIT Delhi, B.Tech Textile Technology (2021–2025)
- **Current job:** Business/Product Analyst – Health Insurance @ Policybazaar (May 2025–Present)
- **Squash:** National Rank #34, Captain IIT Delhi team, 8 Gold / 3 Silver / 1 Bronze

---

## GitHub Setup
- **Repo:** `aayushyad-7734/portfolio` (public)
- **GitHub Pages:** Enabled, deploys from `main` branch, root `/`
- **Auth:** GitHub CLI (`gh`) authenticated via personal access token (scopes: `repo`, `read:org`)
- **Git config:** user.name="Aayush Yadav", user.email="yadaayush7734@gmail.com" (local to this repo)

---

## What's Left / Nice-to-haves
- [ ] Buy a custom domain (e.g., aayushyadav.in) and connect to GitHub Pages
- [ ] Mobile testing on real devices
- [ ] Consider adding a favicon
- [ ] LinkedIn URL verification in contact section
