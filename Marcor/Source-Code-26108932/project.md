# Michael Dell Biography Website — Project Specification

## Project Overview

A professional, multi-page biographical website about **Michael Dell**, founder and CEO of Dell Technologies. The design follows a clean, editorial style inspired by the reference design — minimal color usage, large bold typography, generous whitespace, and a near-monochrome palette. The site must be fully responsive across desktop, tablet, and mobile.

---

## File Structure

```
/project-root
│
├── index.html          → Landing / Hero page
├── main.html           → Michael Dell as CEO & Dell Technologies
├── about.html          → Background, education, personal life
├── contact.html        → Contact form page
├── reference.html      → References & sources used
└── style.css           → Single shared stylesheet for all pages
```

---

## Design System

### Color Palette
| Role | Color | Hex |
|---|---|---|
| Page background | Warm off-white | `#F5F4F0` |
| Primary text | Near-black | `#1A1A1A` |
| Dark section backgrounds | Deep charcoal | `#2A2A2A` |
| Secondary / muted text | Medium grey | `#6B6B6B` |
| Borders & dividers | Light warm grey | `#E0DFDB` |
| Card / panel background | Pure white | `#FFFFFF` |
| Accent highlight | Black | `#000000` |

### Typography
- **Font family:** `'Poppins', sans-serif` — loaded from Google Fonts
- **Display headings (H1):** Poppins Bold or ExtraBold, very large (60–96px desktop), uppercase or mixed case, tight letter-spacing
- **Section headings (H2):** Poppins SemiBold, 36–48px
- **Sub-headings (H3):** Poppins Medium, 22–28px
- **Body text:** Poppins Regular, 16px, line-height 1.7
- **Caption / label text:** Poppins Light, 13px, letter-spacing 0.1em, uppercase

### Spacing & Layout
- Max content width: `1200px`, centered with `auto` margins
- Section padding: `80px 0` on desktop, `48px 0` on tablet, `32px 0` on mobile
- Grid gutters: `24px`
- Cards use `border-radius: 4px` (very subtle) and `box-shadow: 0 2px 12px rgba(0,0,0,0.06)`

---

## Navigation (Shared Across All Pages)

- **Position:** Fixed / sticky at the top, always visible while scrolling
- **Desktop:** Horizontal nav bar with logo on left, nav links on right
- **Tablet & Mobile:** Hamburger menu icon (☰) on right — clicking triggers a **dropdown from the top** (slides down, full width, dark background `#1A1A1A`, white text links)
- Nav links: `Home` | `About` | `Dell & CEO` | `Contact` | `References`
- Active page link is underlined or highlighted
- Nav background: `#FFFFFF` with a subtle bottom border `1px solid #E0DFDB`
- Logo text: "**Michael Dell**" in bold Poppins, black

### Hamburger Menu JavaScript Behavior
```javascript
// Toggle dropdown visibility
hamburgerBtn.addEventListener('click', () => {
  mobileMenu.classList.toggle('open');
  hamburgerBtn.classList.toggle('active'); // Animates ☰ → ✕
});
// Close when a link is clicked
navLinks.forEach(link => link.addEventListener('click', () => {
  mobileMenu.classList.remove('open');
}));
```

---

## Page 1: `index.html` — Landing Page

### Purpose
First impression. Hero section with bold editorial statement, quick intro, and navigation to other sections.

### Sections

#### 1. Hero Section
- **Full-viewport height** (`100vh`)
- Background: Deep charcoal `#2A2A2A`
- Large display text (white): `"MICHAEL DELL"` — massive, bold, editorial
- Subheading: `"Founder & CEO, Dell Technologies"` — smaller, grey
- A horizontal rule / thin line separator (editorial style)
- Birth year and a short one-liner: `"1965 — Present · Visionary. Innovator. Leader."`
- A **scroll-down arrow** (animated bounce, CSS only) that links to next section

#### 2. Quote / Ticker Strip
- Full-width horizontal band, background `#1A1A1A`, white text
- A **scrolling marquee-style quote ticker** using CSS animation (`@keyframes scroll`)
- Quotes/facts cycle horizontally: e.g., `"Revolutionized the PC industry" · "$101B+ Revenue in 2023" · "Started Dell from his dorm room at UT Austin" · "Fortune 500 CEO since age 23"`

#### 3. Quick Stats Cards (Hover Cards)
- 4-column grid on desktop, 2-column on tablet, 1-column on mobile
- Each card: white background, subtle shadow, hover effect (lifts slightly, border turns black)
- Cards:
  1. **Founded Dell** — `1984`
  2. **Company Revenue** — `$101.6B (FY2023)`
  3. **Employees Worldwide** — `120,000+`
  4. **Net Worth** — `~$50 Billion`
- On hover: slight `translateY(-6px)` lift + `box-shadow` deepens

#### 4. Teaser Navigation (Editorial Grid)
- 3-column editorial card grid linking to other pages
- Card 1 → `about.html`: "**His Story**" — background image tinted dark, white overlay text
- Card 2 → `main.html`: "**The CEO & Company**" — same style
- Card 3 → `contact.html`: "**Get In Touch**" — same style
- On hover: scale up slightly + overlay darkens

#### 5. Footer (Shared)
- Background: `#1A1A1A`, white text
- Left: Site name + copyright `© 2024 Michael Dell Biography`
- Right: Quick links (same nav links)
- Center: small note `"Educational project — not affiliated with Dell Technologies"`

---

## Page 2: `main.html` — CEO & Dell Technologies

### Purpose
Covers Michael Dell's professional journey, founding and growing Dell, milestones, and achievements.

### Sections

#### 1. Page Hero
- Smaller than landing hero — `60vh`
- Dark background `#2A2A2A`, white large heading: `"DELL & THE CEO"`
- Subtitle: `"From a dorm room to a Fortune 500 empire"`

#### 2. The Founding Story
- Two-column layout: large text left, image placeholder right
- Scroll-triggered fade-in animation (use `IntersectionObserver`)
- Content: Dell founded in 1984 from Michael Dell's University of Texas dorm room as "PC's Limited", renamed Dell Computer Corporation in 1988, IPO in 1988, went private in 2013, public again in 2018

#### 3. Animated Timeline of Milestones
- Vertical timeline, centered line, alternating left/right cards
- Each milestone card: year (bold, large), event title, short description
- Cards animate in (fade + slide) as user scrolls down
- Key milestones:
  - `1984` — Founded PC's Limited in dorm room, UT Austin
  - `1985` — First self-designed computer; $70M in sales
  - `1988` — IPO; renamed Dell Computer Corporation
  - `1992` — Youngest CEO on Fortune 500 at age 27
  - `1996` — Dell launches website; first to sell PCs online
  - `2001` — Becomes world's largest PC maker
  - `2004` — Steps down as CEO (returns 2007)
  - `2013` — Takes Dell private in $24.9B buyout
  - `2016` — Acquires EMC for $67B (largest tech deal ever)
  - `2018` — Dell Technologies goes public again (NYSE: DELL)
  - `2023` — Revenue exceeds $100B

#### 4. Achievements — Hover Cards Grid
- 3-column grid, responsive to 1-column on mobile
- Each card: icon (use Unicode or simple SVG), title, brief description
- Hover: background goes `#1A1A1A`, text turns white (smooth CSS transition)
- Achievements:
  1. Youngest Fortune 500 CEO (age 27)
  2. Largest tech acquisition in history (EMC, $67B)
  3. Pioneer of direct-to-consumer PC model
  4. Revolutionized build-to-order manufacturing
  5. Dell Foundation philanthropy ($1.9B+ donated)
  6. Member, Business Council & Council on Foreign Relations

#### 5. Image Carousel / Gallery
- A horizontal image slider showing: Dell HQ, Dell products timeline, Michael Dell speaking, early Dell ads
- Navigation arrows (left/right), dot indicators at bottom
- Auto-plays every 4 seconds, pauses on hover
- Use placeholder images with descriptive `alt` text (coding agent should use royalty-free placeholder URLs or `https://placehold.co/` with descriptive labels)

#### 6. Company Today — Split Layout
- Left: Dark background panel `#2A2A2A`, white text, key stats (Revenue, Employees, HQ location, Stock ticker)
- Right: White panel, short paragraph about Dell Technologies today

---

## Page 3: `about.html` — About Michael Dell

### Purpose
Personal background: early life, education, family, social life, philanthropy.

### Sections

#### 1. Page Hero
- `60vh`, dark background `#2A2A2A`
- Heading: `"ABOUT MICHAEL DELL"`
- Subheading: `"The man behind the machine"`

#### 2. Biography Introduction
- Large pull-quote style opening paragraph (bigger font, slight left border accent in black)
- Full biography paragraph below in normal body text
- Scroll-triggered fade-in

#### 3. Early Life & Background
- Two-column: text left, decorative typographic panel right (large birth year `"1965"` in giant grey numerals as background design element)
- Content: Born February 23, 1965, Houston Texas. Father: Alexander Dell (orthodontist), Mother: Lorraine Charlotte (stockbroker). Showed entrepreneurial spirit early — at age 12 earned $2,000 from selling stamps by mail.

#### 4. Education Section
- Card grid (2-column desktop, 1-column mobile)
- Cards styled with a top black border accent
- Education cards:
  1. **Memorial High School**, Houston, TX — Graduated 1983
  2. **University of Texas at Austin** — Pre-medicine, 1983 (dropped out 1984 to run Dell full-time)
  3. **Honorary Doctorate**, University of Tokyo — 2004
  4. **Honorary Doctorate**, Tsinghua University, Beijing — Various honorary recognitions
- Each card: institution name (bold), year, brief note

#### 5. Personal Life & Family
- Clean single-column editorial layout
- Content: Married Susan Lieberman (1989, renamed Susan Dell). 4 children. Lives in Austin, Texas. Known for philanthropy and private lifestyle. Avid technology enthusiast and pilot.

#### 6. Philanthropy
- Light grey background band `#F0EFE9`
- Three stats highlight boxes in a row (like the stats on landing page)
  - `$1.9B+` — Donated via Michael & Susan Dell Foundation
  - `1M+` — Children impacted by foundation programs
  - `50+` — Countries where foundation operates
- Short paragraph on foundation mission: urban education, childhood health, economic stability

#### 7. Quote Block (Full Width)
- Dark background `#1A1A1A`, white large italic quote
- Quote: `"Try never to be the smartest person in the room. And if you are, I suggest you invite smarter people or find a different room."` — Michael Dell
- Centered, with large typographic quotation marks `"` in dark grey as decorative element

---

## Page 4: `contact.html` — Contact Page

### Purpose
A clean, professional contact form page.

### Sections

#### 1. Page Hero
- Smaller hero `40vh`, dark background
- Heading: `"GET IN TOUCH"`
- Subheading: `"Have a question or feedback about this site?"`

#### 2. Contact Layout — Two Column
- **Left column:** Contact information panel (dark background `#2A2A2A`, white text)
  - Section label: "CONTACT INFO" (small caps, letter-spaced)
  - Items: 📧 Email placeholder, 🌐 Website note, 📍 Location: "Online — Educational Project"
  - A short note: `"This is an educational biography website. For official Dell Technologies inquiries, please visit dell.com"`
- **Right column:** Contact form (white background, clean inputs)

#### 3. Contact Form Fields
All fields styled with: bottom-border only (no full border box), clean label above, focus state turns border black
- **Full Name** — text input, required
- **Email Address** — email input, required
- **Subject** — dropdown select: `General Enquiry | Feedback | Correction | Other`
- **Message** — textarea, 5 rows, required
- **Submit Button** — full width, black background, white text, hover: inverts to white background with black border and black text
- Form validation: JavaScript checks all fields are filled before submit; shows inline error messages in red under each empty field
- On successful "submit" (no backend needed — just JS): show a success message `"Thank you! Your message has been noted."` and reset the form

---

## Page 5: `reference.html` — References

### Purpose
Cite all sources used in the website, organized in a card-based layout grouped by resource type.

### Sections

#### 1. Page Hero
- `40vh`, dark background
- Heading: `"REFERENCES & SOURCES"`
- Subheading: `"All resources used in building this website"`

#### 2. Reference Cards — Grouped by Type

Each group has: a section label (uppercase, letter-spaced, with a horizontal divider), followed by a card grid (2-column desktop, 1-column mobile).

**Group 1: 📰 Biographical Information**
Cards linking to:
- Wikipedia — Michael Dell biography
- Encyclopedia Britannica — Michael Dell
- Forbes Profile — Michael Dell
- Bloomberg Profile — Michael Dell

**Group 2: 🏢 Company Information**
- Dell Technologies Official Website (`dell.com`)
- Dell Technologies Annual Report 2023
- Fortune 500 — Dell Technologies listing
- SEC Filings — Dell Technologies

**Group 3: 📸 Images & Media**
- Wikimedia Commons — Michael Dell photos
- Getty Images (referenced only — not used directly)
- Dell Technologies Press Room
- Placehold.co (placeholder images used during development)

**Group 4: 📚 Books & Articles**
- "Direct from Dell" — Michael Dell (1999, HarperBusiness)
- Harvard Business Review — Articles on Dell
- The New York Times — Michael Dell coverage archive
- Wall Street Journal — Dell Technologies reporting

**Group 5: 🎨 Design & Development**
- Google Fonts — Poppins typeface
- Reference design inspiration (editorial biography style)
- MDN Web Docs — HTML/CSS/JS reference

#### Card Design
Each reference card:
- White background, subtle shadow
- Icon/emoji at top-left
- Source name (bold)
- Short description of what it was used for
- URL displayed in grey small text
- Hover: border-left turns solid black (3px), slight background tint

---

## Global Interactive Features

### 1. Scroll-Triggered Fade-In (All Pages)
```javascript
const observer = new IntersectionObserver((entries) => {
  entries.forEach(entry => {
    if (entry.isIntersecting) {
      entry.target.classList.add('visible');
    }
  });
}, { threshold: 0.15 });

document.querySelectorAll('.fade-in').forEach(el => observer.observe(el));
```
CSS:
```css
.fade-in {
  opacity: 0;
  transform: translateY(30px);
  transition: opacity 0.6s ease, transform 0.6s ease;
}
.fade-in.visible {
  opacity: 1;
  transform: translateY(0);
}
```

### 2. Smooth Scroll
```css
html {
  scroll-behavior: smooth;
}
```

### 3. Back-to-Top Button
- Fixed position, bottom-right, appears after scrolling 300px
- Black circle button with ↑ arrow, white icon
- Smooth scroll to top on click
- Fade in/out with CSS transition

### 4. Animated Timeline (main.html)
- Each `.timeline-item` starts invisible, slides in from left or right on scroll using `IntersectionObserver`

### 5. Image Carousel (main.html)
- Pure JS — no libraries
- Auto-advance every 4000ms, pause on hover (`mouseenter`/`mouseleave`)
- Left/right arrow click moves one slide

### 6. Quote Ticker (index.html)
```css
@keyframes ticker-scroll {
  0%   { transform: translateX(100%); }
  100% { transform: translateX(-100%); }
}
.ticker-track {
  animation: ticker-scroll 25s linear infinite;
  white-space: nowrap;
}
```

---

## Responsive Breakpoints

| Breakpoint | Target |
|---|---|
| `≥ 1200px` | Desktop (full layout) |
| `768px – 1199px` | Tablet (hamburger appears, 2-col grids) |
| `< 768px` | Mobile (1-col layout, stacked sections) |

Key mobile adjustments in `style.css`:
- Hamburger menu replaces horizontal nav
- All multi-column grids collapse to single column
- Hero font sizes reduce significantly (use `clamp()`)
- Timeline becomes single-column left-aligned
- Carousel arrows move inside the image

---

## CSS Architecture (`style.css`)

Organize the single CSS file in this order with clear section comments:

```css
/* ===========================
   1. CSS Variables & Root
   =========================== */

/* ===========================
   2. Reset & Base Styles
   =========================== */

/* ===========================
   3. Typography
   =========================== */

/* ===========================
   4. Navigation & Hamburger
   =========================== */

/* ===========================
   5. Hero Sections
   =========================== */

/* ===========================
   6. Cards & Hover Effects
   =========================== */

/* ===========================
   7. Timeline
   =========================== */

/* ===========================
   8. Carousel / Gallery
   =========================== */

/* ===========================
   9. Quote & Ticker Strip
   =========================== */

/* ===========================
   10. Contact Form
   =========================== */

/* ===========================
   11. Reference Cards
   =========================== */

/* ===========================
   12. Footer
   =========================== */

/* ===========================
   13. Back-to-Top Button
   =========================== */

/* ===========================
   14. Animations & Transitions
   =========================== */

/* ===========================
   15. Responsive — Tablet
   =========================== */

/* ===========================
   16. Responsive — Mobile
   =========================== */
```

### CSS Root Variables
```css
:root {
  --bg-primary: #F5F4F0;
  --bg-dark: #2A2A2A;
  --bg-darker: #1A1A1A;
  --bg-white: #FFFFFF;
  --bg-light-grey: #F0EFE9;

  --text-primary: #1A1A1A;
  --text-white: #FFFFFF;
  --text-muted: #6B6B6B;
  --text-accent: #000000;

  --border-color: #E0DFDB;
  --border-dark: #000000;

  --font-family: 'Poppins', sans-serif;

  --transition-speed: 0.3s;
  --border-radius: 4px;
  --max-width: 1200px;

  --shadow-card: 0 2px 12px rgba(0, 0, 0, 0.06);
  --shadow-card-hover: 0 8px 32px rgba(0, 0, 0, 0.12);
}
```

---

## Image Placeholder Strategy

Since this is an educational project without licensed images, use `placehold.co` URLs:

```html
<!-- Example usage -->
<img src="https://placehold.co/800x500/2A2A2A/F5F4F0?text=Michael+Dell" alt="Michael Dell" />
<img src="https://placehold.co/400x300/1A1A1A/FFFFFF?text=Dell+HQ+Austin" alt="Dell HQ" />
```

All `img` tags must have descriptive `alt` text. Images should have `width: 100%` and `height: auto` unless inside a fixed-height container.

---

## Coding Standards & Notes

1. **No external CSS frameworks** — pure vanilla CSS only (no Bootstrap, no Tailwind)
2. **No external JS libraries** — pure vanilla JavaScript only (no jQuery)
3. **Google Fonts** is the only external dependency — load in `<head>` of every HTML file:
   ```html
   <link rel="preconnect" href="https://fonts.googleapis.com">
   <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700;800;900&display=swap" rel="stylesheet">
   ```
4. **`style.css`** must be linked in all HTML pages: `<link rel="stylesheet" href="style.css">`
5. All interactive JS (back-to-top, carousel, timeline, fade-in, hamburger, contact form validation) should be either inline `<script>` at bottom of each page or a shared `script.js` file (coder's choice — keep it organized)
6. All pages must share the **same nav** and **same footer** HTML structure
7. Use **semantic HTML**: `<header>`, `<nav>`, `<main>`, `<section>`, `<article>`, `<footer>`, `<figure>`, `<time>`
8. Add `meta viewport` tag to all HTML files for mobile responsiveness
9. All information used must be factually accurate to Michael Dell's real biography

---

## Deliverables Checklist

- [ ] `index.html` — Landing page with hero, ticker, stats cards, teaser nav, footer
- [ ] `main.html` — CEO page with hero, founding story, animated timeline, achievements grid, carousel, company stats
- [ ] `about.html` — Bio page with hero, intro, early life, education cards, personal life, philanthropy stats, quote block
- [ ] `contact.html` — Contact page with hero, two-column layout, validated contact form
- [ ] `reference.html` — Reference page with hero, card groups by type
- [ ] `style.css` — Complete shared stylesheet, organized with comments, CSS variables, fully responsive
- [ ] All interactive features working: hamburger dropdown, scroll fade-in, back-to-top, timeline animation, image carousel, quote ticker, hover effects, form validation

---

*Project compiled for: Michael Dell Biography Website · Educational Purpose · Version 1.0*