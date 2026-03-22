# Portfolio Project Checkpoint
_Captured before context compaction — use this to resume in a new agent_

---

## Project Overview
Building a personal portfolio website for **Aayush Yadav** (Product & Business Analyst, IIT Delhi grad, ex-national squash player).

**Portfolio file location:** `/Users/aayushyadav/Downloads/final_portfolio/portfolio.html`
**All assets are in:** `/Users/aayushyadav/Downloads/final_portfolio/`

---

## Design
- **Theme:** Dark background (`#0a0a0a`), light pink accent (`#e8a0b4`), off-white text (`#f0ece6`)
- **Fonts:** Instrument Serif (headings), DM Sans (body), JetBrains Mono (labels/tags)
- **Features:** Custom pink cursor dot, scroll-reveal animations, frosted glass nav

---

## Nav Structure
Fixed top nav with:
- Logo: `aayush.` (left)
- Tabs: About · Experience · Projects · Skills · Recognition · Gallery (center)
- **Resume button:** Pink rectangle, black text, rightmost — opens resume modal on click

---

## Page Sections (in order)
1. **Hero** — Photo (`image.jpg`), name, title, tagline, fade-in animations
2. **About** (`#about`) — Bio, 3 key stats (25% V2L, 50% training time, 300+ agents), detail cards (Education, Current Role, Athletics)
3. **Experience** (`#experience`) — Timeline with Policybazaar (current) + Policybazaar internship (PPO)
4. **Projects** (`#projects`) — 2×2 grid, each card has hover "View More →" overlay that opens a modal
5. **Skills** (`#skills`) — Pill tags
6. **Recognition** (`#awards`) — 4 award items + floating horizontal photo carousel (`#gallery`)
7. **Contact** (`#contact`) — "Let's build something great" + email/LinkedIn/phone

---

## Project Modals ("View More")
Each project card opens a modal with: Overview, Design Approach, Tools & Stack, Impact.
**Challenges section was intentionally removed.**

### Modal content per project:
- **PROJECT 01 — Mindlessly:** Chrome extension. Has a "How It Works" section with 3 screenshots showing the flow: `mindlessly-1.jpg` (intention), `mindlessly-2.jpg` (timer), `mindlessly-3.jpg` (time's up). Click screenshot = lightbox zoom.
- **PROJECT 02 — AI Sales Coach:** NotebookLM + transcription API. Has "Output Preview" section with `call-score.jpg` showing the call analysis dashboard.
- **PROJECT 03 — Data Intelligence KB:** Custom GPT + SQL knowledge base.
- **PROJECT 04 — Social Proof MVP:** Claude Code + pincode customer density.

### Modal JS functions:
```javascript
openModal(id)   // e.g. openModal('modal-01')
closeModal()
openLightbox(src)
closeLightbox()
```

---

## Photo Gallery (Recognition section)
**Type:** Horizontal auto-scrolling carousel with blur/focus effect
- 1 center image in focus (sharp, scaled up), side images blurred
- Auto-scrolls every 2.8s, pauses 4s on manual scroll
- Scroll wheel to navigate, click to focus, click focused image = lightbox
- 11 images in `medals/` subfolder (converted HEIC → JPG)
- JS functions: `galleryGoTo(index)`

---

## Resume
- **Resume button in nav** → opens modal with PDF preview
- PDF lazy-loads only when modal opens (to avoid Safari's PDF toolbar bug)
- Download button inside modal
- File: `resume.pdf`
- Modal iframe id: `resumeIframe`
- JS: `openResumeModal()`, `closeResumeModal()`

---

## Asset Files in `/final_portfolio/`
```
portfolio.html          ← main file
image.jpg               ← hero profile photo
resume.pdf              ← CV (APM.pdf copy)
call-score.jpg          ← AI Sales Coach output preview
mindlessly-1.jpg        ← Intention screenshot
mindlessly-2.jpg        ← Timer screenshot
mindlessly-3.jpg        ← Time's up screenshot
medals/                 ← 11 trophy/medal photos for gallery
  IMG_0363.jpg
  IMG_1560.jpg
  IMG_3377.JPG
  IMG_3488 2.jpg
  IMG_6650.jpg
  IMG_7721.jpg
  IMG_8604.jpg
  IMG_8802.jpg
  55640252-...JPG
  9255ddc6-...JPG
  CF6351C0-...JPG
```

---

## Known Open Issue — Safari Modal Scroll
**Problem:** The "View More" project modals scroll fine in Chrome but NOT in Safari.

**What was tried (none fully worked):**
1. `overflow-y: auto` → works Chrome, not Safari
2. Flex column layout + `min-height: 0` on body → broke Chrome too
3. `position: fixed` on body for scroll lock → broke Safari modal scroll context
4. `overflow-y: scroll` + `touch-action: pan-y` + removed `position: sticky` from header → latest attempt, unverified

**Current modal CSS state:**
```css
.modal {
  position: fixed;
  top: 50%; left: 50%;
  transform: translate(-50%, -46%);
  width: min(680px, 92vw);
  max-height: 90vh;
  overflow-y: scroll;
  -webkit-overflow-scrolling: touch;
  overscroll-behavior: contain;
  touch-action: pan-y;
  ...
}
.modal-header { /* no position: sticky — removed to fix Safari */ }
.modal-body { padding, flex column, gap }
```

**Current JS scroll lock:**
```javascript
document.body.style.overflow = 'hidden';  // on open
document.body.style.overflow = '';         // on close
```

**Next step suggested by user:**
Install the `dev-browser` skill from:
`https://github.com/SawyerHood/dev-browser/tree/main/skills/dev-browser`
…then use it to actually test and verify the Safari scroll fix in a real browser before accepting.

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

## What's Left / Nice-to-haves
- [ ] Fix Safari modal scroll (primary open issue)
- [ ] Deploy the portfolio online (Netlify / GitHub Pages / Vercel suggested)
- [ ] Fix LinkedIn URL in contact section (currently correct: linkedin.com/in/aayush-yadav-38a880229)
- [ ] Mobile responsiveness check
