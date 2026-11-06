# Paul Gray Brand & Design Bible

> **Version:** 1.0
> **Last Updated:** 6 November 2026
> **Purpose:** Single source of truth for brand identity, design system, technical stack, and functional patterns across all Paul Gray digital properties

---

## Table of Contents

1. [Brand Architecture](#1-brand-architecture)
2. [Visual Identity System](#2-visual-identity-system)
3. [Typography System](#3-typography-system)
4. [Color System](#4-color-system)
5. [Component Library](#5-component-library)
6. [Voice & Tone Guidelines](#6-voice--tone-guidelines)
7. [Technical Stack & Standards](#7-technical-stack--standards)
8. [Functional Patterns](#8-functional-patterns)
9. [Content Standards](#9-content-standards)
10. [Implementation Checklist](#10-implementation-checklist)

---

## 1. Brand Architecture

### 1.1 Brand Hierarchy

**Parent Brand:** Paul Gray
**Tagline:** Swim Coach · Tempe, Sydney

**Sub-brands (current strategy: coach community first, then client-facing):**

1. **Coach Community** (unnamed, build first)
   - **Audience:** Swim instructors, teachers, and coaches
   - **Purpose:** Authority-building, methodology sharing, PASS framework dissemination
   - **Tone:** Peer-to-peer, practical, technical depth with human insight
   - **Platform:** Skool community (name TBD: *On The Deck* or *The Coaches' Lane*)

2. **Paul Gray Performance** (client brand, later)
   - **Audience:** Parents of swimmers aged 5–17 (recreational + competitive)
   - **Purpose:** Movement/conditioning, technique, data tracking
   - **Tone:** Empowering, evidence-based, parent-friendly
   - **Pillars:**
     - Movement & conditioning (FMS-gated)
     - Swimming technique & conditioning
     - Consistent data tracking
   - **Service Tiers:** Free lead magnet → Low-cost community → Premium 1:1/camps/workshops

3. **Before The Blocks** (swimmer/parent community, reserved)
   - **Audience:** Swimmers and their parents
   - **Purpose:** Community, resources, trust-inheritance from coach network
   - **Status:** Reserved until coach community succeeds

### 1.2 Brand Positioning

**Differentiator:** Technical and scientific rigor (CSS, USRPT, periodisation, biomechanics) delivered through the human layer (discipline, connection, trust). *The human layer is what makes the science land.*

**Core Philosophy:**
- Environment before technique
- Discipline → Connection → Trust (in that order)
- Resilience and capacity language (not "injury reduction")
- Upstream strength/mobility work improves every pathway

**Hard Rules:**
- No private kids coaching under Before The Blocks until coach community succeeds
- No dryland/conditioning offers publicly until FMS + ASCA Level 1 (S&C) credentials held
- Never approach Col Jones clients for private business
- First names/initials only in shareable swimmer data

---

## 2. Visual Identity System

### 2.1 Logo & Lockup

**Primary Lockup:**
```
PAUL GRAY
Swim Coach · Tempe, Sydney
```

**Typography:**
- Name: Barlow Condensed 800, uppercase, letterspacing 0.02em
- Tagline: Inter 500, sentence case, 0.06em letterspacing, smaller size (~0.62em relative)

**Color:**
- Name: `--col-ink` (default text color)
- Tagline: `--col-water` (brand accent)

**Spacing:**
- 3px vertical gap between name and tagline
- Line-height: 1 for name, 1.4 for tagline

### 2.2 Grid & Layout

**Container System:**
```css
.container {
  width: 100%;
  max-width: var(--max-width);  /* 900px */
  margin-inline: auto;
  padding-inline: var(--gutter); /* clamp(1.25rem, 5vw, 3rem) */
}
```

**Vertical Rhythm:**
- Section padding: `var(--section-v)` = `clamp(3.5rem, 8vw, 6.5rem)`
- Internal spacing: multiples of 0.25rem (4px baseline grid)

**Responsive Breakpoints:**
- Mobile-first approach
- Major breakpoint: `700px` (tablet/desktop split)
- Secondary: `480px` (small mobile)
- Secondary: `600px` (component-specific)

**Grid Patterns:**
- Hero: 1fr mobile, 7fr 5fr desktop (text-heavy left, image right)
- Credentials/stats: `repeat(auto-fit, minmax(190px, 1fr))`
- Contact: 1fr mobile, 5fr 7fr desktop (info left, form right)

### 2.3 Imagery Guidelines

**Profile Photos:**
- Aspect ratio: 4:5 (portrait)
- Border-radius: 8px (standard), 50% (avatar)
- Object-fit: cover
- Max-width: 320px on mobile, responsive on desktop

**Hosting:**
- Platform: Cloudinary
- Current CDN: `res.cloudinary.com/dr6ncein2/image/upload/`
- Format: WebP preferred

**Alt Text:**
- Always descriptive: "Paul Gray" not "Profile picture"

---

## 3. Typography System

### 3.1 Font Stack

**Display/Headings:**
```css
--font-display: 'Barlow Condensed', sans-serif;
```
- Weights: 700 (bold), 800 (extrabold)
- Use: H1, H2, large headlines, numbers, logo
- Transform: uppercase (primary use case)
- Letter-spacing: -0.01em to 0.02em depending on size

**Body/UI:**
```css
--font-body: 'Inter', sans-serif;
```
- Weights: 400 (regular), 500 (medium), 600 (semibold), 400 italic
- Use: Body text, buttons, forms, navigation
- Letter-spacing: default (body), 0.1em (labels/eyebrows)

**Loading:**
```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Barlow+Condensed:wght@700;800&family=Inter:ital,wght@0,400;0,500;0,600;1,400&display=swap" rel="stylesheet">
```

### 3.2 Type Scale

**Headings:**
```css
/* H1 - Hero headlines */
font-family: var(--font-display);
font-size: clamp(2.5rem, 8vw, 4.75rem);
font-weight: 800;
line-height: 0.95;
letter-spacing: -0.01em;
text-transform: uppercase;

/* H2 - Section headlines */
font-family: var(--font-display);
font-size: clamp(2rem, 6vw, 3.5rem);
font-weight: 800;
line-height: 0.95;
text-transform: uppercase;

/* H2 - Resource group headings */
font-family: var(--font-display);
font-size: 1.35rem;
font-weight: 800;
letter-spacing: 0.01em;
text-transform: uppercase;
```

**Body Text:**
```css
body {
  font-family: var(--font-body);
  font-size: clamp(0.95rem, 1.5vw, 1.05rem);
  line-height: 1.65;
}
```

**Labels & Eyebrows:**
```css
.section-label {
  font-size: 0.72rem;
  font-weight: 600;
  letter-spacing: 0.1em;
  text-transform: uppercase;
  color: var(--col-muted);
}
```

**Badges:**
```css
.badge-ss {
  font-size: 0.68rem;
  font-weight: 600;
  letter-spacing: 0.03em;
}
```

### 3.3 Emphasis Patterns

**Italics in Headlines:**
- Use `<em>` with `font-style: normal; color: var(--col-water);` for brand accent
- Example: "Building *what's next*" → "what's next" in water blue

---

## 4. Color System

### 4.1 Core Palette

**Light Mode (default):**
```css
:root {
  /* Neutrals */
  --col-paper:        #F4F3EF;  /* Background, cream tone */
  --col-ink:          #0C1820;  /* Primary text, navy */
  --col-surface:      #E8E5DE;  /* Cards, panels, subtle */
  --col-muted:        #5A7580;  /* Secondary text, labels */

  /* Brand */
  --col-water:        #0087A8;  /* Primary accent, links, CTAs */
  --col-water-hover:  #006888;  /* Hover/active states */
  --col-water-light:  #D0ECF3;  /* Backgrounds, badges */

  /* Borders */
  --col-border:       rgba(0, 135, 168, 0.14);  /* Subtle dividers */
}
```

**Dark Mode:**
```css
@media (prefers-color-scheme: dark) {
  :root {
    --col-paper:       #0C1820;  /* Dark navy background */
    --col-ink:         #EEF1EE;  /* Light text */
    --col-surface:     #131E28;  /* Elevated surfaces */
    --col-muted:       #7AA4B0;  /* Muted text */

    --col-water:       #00B8D9;  /* Brighter accent for contrast */
    --col-water-hover: #0095B0;
    --col-water-light: #0D2232;  /* Dark teal background */

    --col-border:      rgba(0, 184, 217, 0.18);
  }
}
```

**Dark Teaser Section (coach community):**
```css
--col-dark-bg:      #0C1820;  /* Deep navy (light mode) or #0A2030 (dark mode) */
--col-dark-text:    #F4F3EF;  /* Light cream text */
--col-dark-muted:   #7FA4B0;  /* Muted on dark */
--col-dark-border:  rgba(255, 255, 255, 0.12);
--col-dark-input:   rgba(255, 255, 255, 0.09);
```

### 4.2 Meta Theme Colors

```html
<meta name="theme-color" content="#F4F3EF" media="(prefers-color-scheme: light)">
<meta name="theme-color" content="#0C1820" media="(prefers-color-scheme: dark)">
```

### 4.3 Color Usage Rules

**Text Hierarchy:**
1. Primary content: `--col-ink`
2. Secondary/supporting: `--col-muted`
3. Interactive elements: `--col-water`
4. Hover states: `--col-water-hover`

**Backgrounds:**
- Page: `--col-paper`
- Cards/surfaces: `--col-surface` (subtle elevation)
- Highlight panels: `--col-water-light` (credentials, stats)
- Dark sections: `--col-dark-bg` (coach community teaser)

**Borders:**
- Default: `--col-border` (1px or 1.5px)
- Focus states: `--col-water` (2px outline, 2-3px offset)

**Never:**
- Use pure black (#000) or pure white (#fff) for text
- Use colors outside the defined palette without documenting
- Override dark mode with hardcoded values

---

## 5. Component Library

### 5.1 Buttons

**Primary Button:**
```css
.btn--primary {
  background-color: var(--col-water);
  color: #fff;
  padding: 0.75em 1.5em;
  font-size: 0.9rem;
  font-weight: 600;
  border-radius: 5px;
  transition: background-color 0.2s var(--ease-out), transform 0.15s var(--ease-out);
}
.btn--primary:hover {
  background-color: var(--col-water-hover);
  transform: translateY(-1px);
}
.btn--primary:active {
  transform: translateY(0);
}
```

**Ghost Button:**
```css
.btn--ghost {
  background-color: transparent;
  color: var(--col-water);
  border: 1.5px solid var(--col-water);
}
.btn--ghost:hover {
  background-color: var(--col-water);
  color: #fff;
}
```

**Modifiers:**
- `.btn--full`: `width: 100%; justify-content: center;`
- Nav CTA: `.nav__cta { font-size: 0.85rem; padding: 0.6em 1.2em; }`

**Arrow Convention:**
- Use `→` (rightwards arrow, U+2192) for forward actions: "Get in touch →", "View →"

### 5.2 Forms

**Input Fields:**
```css
input, textarea {
  width: 100%;
  padding: 0.8em 1em;
  background: var(--col-paper);
  border: 1.5px solid var(--col-border);
  border-radius: 5px;
  font-family: var(--font-body);
  font-size: 0.95rem;
  color: var(--col-ink);
  transition: border-color 0.2s var(--ease-out);
}
input:focus, textarea:focus {
  border-color: var(--col-water);
  outline: none;
}
```

**Dark Mode Forms:**
```css
@media (prefers-color-scheme: dark) {
  input, textarea {
    background: var(--col-dark-bg);
    border-color: rgba(0, 184, 217, 0.2);
  }
}
```

**Labels:**
```css
.form-label {
  font-size: 0.8rem;
  font-weight: 600;
  color: var(--col-muted);
}
```

**Honeypot:**
```css
.form-honeypot {
  display: none;
}
```

**Success State:**
```css
.form-success {
  font-size: 1rem;
  color: var(--col-water);
  font-weight: 500;
}
```

### 5.3 Navigation

**Header:**
```css
.nav {
  border-bottom: 1px solid var(--col-border);
}
.nav__inner {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding-block: 1.25rem;
}
```

**Navigation Links:**
- Color: `var(--col-water)`
- Font-size: `0.9rem`
- Font-weight: `500`
- No text-decoration, underline on hover

### 5.4 Cards & Badges

**Credential Badge:**
```css
.cred-badge {
  display: flex;
  align-items: center;
  gap: 0.75rem;
  padding: 0.9rem 1rem;
  background: rgba(255, 255, 255, 0.72);
  border: 1px solid var(--col-border);
  border-radius: 6px;
}
@media (prefers-color-scheme: dark) {
  .cred-badge {
    background: rgba(12, 24, 32, 0.7);
  }
}
```

**Resource Item:**
```css
.resource-item {
  display: flex;
  flex-wrap: wrap;
  align-items: baseline;
  justify-content: space-between;
  gap: 0.5rem 1rem;
  padding: 0.9rem 1.1rem;
  background: var(--col-surface);
  border-radius: 6px;
}
```

**Stat Card:**
```css
.stat-card {
  padding: 1.1rem 1.2rem;
  background: rgba(255, 255, 255, 0.72);
  border: 1px solid var(--col-border);
  border-radius: 6px;
}
.stat-card__num {
  font-family: var(--font-display);
  font-weight: 800;
  font-size: 2rem;
  color: var(--col-ink);
  line-height: 1;
}
.stat-card__num span {
  color: var(--col-water);  /* Highlight number */
}
```

### 5.5 Accordion

```css
.accordion-item {
  margin-bottom: 1rem;
  border: 1px solid var(--col-border);
  border-radius: 6px;
  background: var(--col-surface);
  overflow: hidden;
}
.accordion-header {
  padding: 1.1rem 1.25rem;
  font-weight: 600;
  cursor: pointer;
  list-style: none;
  display: flex;
  justify-content: space-between;
  transition: background-color 0.2s var(--ease-out);
}
.accordion-header::after {
  content: '+';
  font-size: 1.5rem;
  font-weight: 700;
  color: var(--col-water);
  transition: transform 0.2s var(--ease-out);
}
.accordion-item[open] .accordion-header::after {
  transform: rotate(45deg);
}
.accordion-header:hover {
  background-color: var(--col-water-light);
}
```

### 5.6 Lane Rope Divider

```css
.lane-rope {
  position: relative;
  width: 100%;
  height: 22px;
  margin-block: clamp(2rem, 5vw, 3.5rem);
}
.lane-rope::before {
  content: '';
  position: absolute;
  inset-inline: 0;
  top: 50%;
  height: 1.5px;
  background: var(--col-water);
  opacity: 0.3;
  transform: translateY(-50%);
}
.lane-rope::after {
  content: '';
  position: absolute;
  inset: 0;
  background-image: radial-gradient(circle, var(--col-water) 4.5px, transparent 4.5px);
  background-size: 36px 22px;
  background-repeat: repeat-x;
  background-position: 0 50%;
}
```

**Usage:** Visual divider between major sections, swimming-themed brand element.

### 5.7 Footer

```css
.footer {
  padding-block: 2rem;
  border-top: 1px solid var(--col-border);
}
.footer__inner {
  display: flex;
  flex-wrap: wrap;
  align-items: center;
  justify-content: space-between;
  gap: 0.875rem;
}
.footer__logo {
  font-family: var(--font-display);
  font-size: 1.05rem;
  font-weight: 800;
  text-transform: uppercase;
  letter-spacing: 0.04em;
}
.footer__logo span {
  font-family: var(--font-body);
  font-size: 0.65rem;
  font-weight: 500;
  color: var(--col-water);
  margin-left: 0.5rem;
  text-transform: none;
}
.footer__meta {
  display: flex;
  flex-wrap: wrap;
  gap: 1.25rem;
  font-size: 0.78rem;
  color: var(--col-muted);
}
```

---

## 6. Voice & Tone Guidelines

### 6.1 Brand Voice (Universal)

**Attributes:**
- **Direct:** Get to the point, no fluff
- **Grounded:** Evidence-based, not hype-driven
- **Human:** Technical depth + practical empathy
- **Confident:** Authority without arrogance
- **Australian English:** Spelling, phrasing, localization

### 6.2 Tone by Audience

**Coach Community:**
- Peer-to-peer, assuming competence
- Technical terminology welcome
- Share the "why" behind methodology
- Acknowledge complexity of human factors
- Example: "Discipline and structure first. Black and white rules. It's easier to loosen the rope than tighten it later."

**Parents (Paul Gray Performance):**
- Empowering, not prescriptive
- Demystify without dumbing down
- Resilience and capacity language (not "reduces injury risk")
- "Your child" not "your kid" in formal contexts
- Example: "Kids now arrive at learn-to-swim weaker and less mobile than past generations. Building strength and mobility upstream improves every pathway."

**General Public (Holding Site):**
- Professional, approachable
- Clear service offering
- No jargon without explanation
- Example: "I coach learn-to-swim through competitive squads at Col Jones Swim Fitness."

### 6.3 Writing Rules

**Do:**
- Use sentence case for most headings (except brand lockup/nav)
- Write in active voice
- Use contractions naturally ("I'll", "it's", "what's")
- Lead with benefits, explain features second
- Use Australian spelling (e.g., "programme" not "program" for training plans)

**Don't:**
- Use superlatives without evidence ("best", "revolutionary")
- Make health/injury claims without credentials
- Fabricate testimonials (use "founding client" framing until real quotes exist)
- Write in third person about Paul ("Paul Gray is..." → "I am...")
- Over-explain; trust reader intelligence

**Emoji Use:**
- Sparingly, only where contextually appropriate
- Swimming-related: 🏊, 🥇, 🏆 (sparingly)
- Flags: Use for athlete nationalities on records page
- Never in professional correspondence or legal text

### 6.4 Call-to-Action Patterns

**Primary CTAs:**
- "Get in touch →"
- "What I recommend →"
- "Send message →"
- "View →" (resource links)

**Waitlist/Newsletter:**
- "Get notified when it's ready"
- "Join the waitlist"
- "No spam. Updates only when there's something ready."

**Form Microcopy:**
- Placeholder: "your@email.com", "First and last name", "What's on your mind?"
- Success: "Received – I'll be in touch soon. 👋"
- Error: "Something went wrong – please email directly at paul@paulgray.com.au"

---

## 7. Technical Stack & Standards

### 7.1 Core Stack

**Hosting & Infrastructure:**
- **Static hosting:** Cloudflare Pages
- **DNS:** Cloudflare (domains: paulgray.com.au, paulgray.co, paulgray.coach)
- **Version control:** GitHub (repos: personal site, PASS, dashboard)
- **Access control:** Cloudflare Access (for PASS private content)

**Backend Services:**
- **Forms:** Web3Forms (contact forms)
- **Email capture:** ConvertKit (newsletter `b01b595d85`, waitlist forms)
- **Database:** Cloudflare D1 (future dashboard: Coach DB + Me DB)
- **Functions:** Cloudflare Functions (serverless, future dashboard logic)

**Media:**
- **Images:** Cloudinary (`res.cloudinary.com/dr6ncein2/`)
- **Video:** Vimeo (future, technique analysis)

**Community & Content:**
- **Community platform:** Skool
- **Documentation:** MkDocs Material (PASS repo)
- **Email:** Google Workspace (paul@paulgray.com.au)

**Coaching Tools:**
- SWIMDeck, Swim Central, iClassPro, Deputy (Col Jones systems)
- Kinovea (video analysis)
- Finis 3X100 stopwatch
- Google Sheets (session planning, time tracking)

### 7.2 Code Standards

**HTML:**
- Semantic HTML5 elements (`<header>`, `<main>`, `<section>`, `<nav>`, `<footer>`)
- ARIA labels for accessibility (`aria-label`, `aria-labelledby`, `role`)
- Meta tags: description, viewport, theme-color, Open Graph (future)
- `lang="en-AU"` on `<html>`

**CSS:**
- Custom properties (CSS variables) for all design tokens
- Mobile-first responsive design
- `clamp()` for fluid typography and spacing
- BEM-inspired naming (`.block__element--modifier`)
- Avoid `!important` (exception: `prefers-reduced-motion`)
- Logical properties: `padding-block`, `margin-inline`, `inset`

**JavaScript:**
- Vanilla JS, no framework (current sites)
- Progressive enhancement (forms work without JS)
- Async/await for API calls
- Event delegation where appropriate
- Accessible focus management

**File Structure:**
```
/
├── index.html
├── records.html
├── resources.html
├── links.html
├── style.css
├── paul-gray-brand-design-bible.md (this file)
├── 6-nov-2026-swimbiz-master-context.md
└── Updates/ (archive folder)
```

### 7.3 Performance Standards

**Targets:**
- Lighthouse Performance: >90
- First Contentful Paint: <1.5s
- Largest Contentful Paint: <2.5s
- Cumulative Layout Shift: <0.1

**Tactics:**
- Preconnect to font hosts
- WebP images, lazy loading where appropriate
- Minimal external dependencies
- Inline critical CSS for above-fold content (future optimization)

### 7.4 Accessibility Standards

**WCAG 2.1 Level AA Compliance:**
- Color contrast: 4.5:1 minimum for normal text, 3:1 for large text
- Keyboard navigation: all interactive elements focusable
- Focus indicators: 2px outline, 2-3px offset, `var(--col-water)`
- Form labels: explicit `<label for="">` associations
- Alt text: descriptive for meaningful images
- Skip links (future): allow keyboard users to skip navigation

**Reduced Motion:**
```css
@media (prefers-reduced-motion: reduce) {
  * {
    animation-duration: 0.01ms !important;
    transition-duration: 0.01ms !important;
  }
}
```

**Color Scheme Support:**
```css
html {
  color-scheme: light dark;
}
```

### 7.5 SEO Standards

**Every Page Must Have:**
- Unique `<title>` (50-60 characters, brand at end)
- Meta description (150-160 characters)
- Semantic heading hierarchy (one `<h1>` per page)
- Descriptive URLs (lowercase, hyphens, no underscores)

**Current Title Patterns:**
- Homepage: "Paul Gray | Swim Coach · Tempe, Sydney"
- Records: "Swimming Records | Paul Gray - Swim Coach"
- Resources: "What I Recommend | Paul Gray"
- Links: "Paul Gray - Links"

**Future:**
- Open Graph tags for social sharing
- Structured data (Person, LocalBusiness schema.org)
- XML sitemap (Cloudflare Pages auto-generates)

---

## 8. Functional Patterns

### 8.1 Form Handling

**Contact Form Pattern (Web3Forms):**

```html
<form class="contact-form" id="contactForm">
  <input type="hidden" name="access_key" value="[WEB3FORMS_KEY]">
  <input type="hidden" name="subject" value="New enquiry from paulgray.com.au">
  <input type="hidden" name="from_name" value="Paul Gray site - contact form">

  <!-- Honeypot -->
  <input type="checkbox" name="botcheck" class="form-honeypot" tabindex="-1" autocomplete="off">

  <div class="form-row">
    <label class="form-label" for="cf-name">Your name</label>
    <input type="text" id="cf-name" name="name" placeholder="First and last name" required>
  </div>

  <div class="form-row">
    <label class="form-label" for="cf-email">Email address</label>
    <input type="email" id="cf-email" name="email" placeholder="your@email.com" required>
  </div>

  <div class="form-row">
    <label class="form-label" for="cf-message">Message</label>
    <textarea id="cf-message" name="message" rows="5" placeholder="What's on your mind?" required></textarea>
  </div>

  <button type="submit" class="btn btn--primary btn--full">Send message →</button>
</form>
```

**JavaScript Handler:**

```javascript
const contactForm = document.getElementById('contactForm');
if (contactForm) {
  contactForm.addEventListener('submit', async (e) => {
    e.preventDefault();
    const submitBtn = contactForm.querySelector('[type="submit"]');
    const originalText = submitBtn.textContent;
    submitBtn.textContent = 'Sending…';
    submitBtn.disabled = true;

    const formData = new FormData(contactForm);
    const object = Object.fromEntries(formData);
    const json = JSON.stringify(object);

    try {
      const res = await fetch('https://api.web3forms.com/submit', {
        method: 'POST',
        headers: { 'Content-Type': 'application/json', Accept: 'application/json' },
        body: json
      });
      const result = await res.json();

      if (result.success) {
        contactForm.closest('.contact__form-wrapper').innerHTML =
          '<div class="form-success-block"><p class="form-success">Received - I\'ll be in touch soon. 👋</p></div>';
      } else {
        throw new Error(result.message || 'Submission failed');
      }
    } catch (err) {
      submitBtn.textContent = originalText;
      submitBtn.disabled = false;
      alert('Something went wrong - please email directly at paul@paulgray.com.au');
    }
  });
}
```

**Future Enhancements:**
- hCaptcha toggle for spam prevention
- Field validation before submit
- Success message with auto-redirect option

### 8.2 Email Capture Pattern (ConvertKit)

**Waitlist Embed:**

```html
<script async data-uid="[KIT_FORM_UID]" src="https://paulgray.kit.com/[KIT_FORM_UID]/index.js"></script>
```

**Styling:**
- Inherit button styles from `.btn--primary`
- Match form field styles
- Privacy note below: "No spam. Updates only when there's something ready."

**List:**
- Newsletter ID: `b01b595d85`
- Waitlist form UID: pending

### 8.3 Navigation Pattern

**Standard Navigation (All Pages):**

```html
<header class="nav" role="banner">
  <div class="container nav__inner">
    <a href="index.html" class="nav__logo" aria-label="Paul Gray - home">
      Paul Gray
      <span>Swim Coach · Tempe, Sydney</span>
    </a>
    <nav style="display: flex; gap: 1rem; align-items: center;">
      <a href="records.html" style="color: var(--col-water); text-decoration: none; font-size: 0.9rem; font-weight: 500;">Swimming Records</a>
      <a href="resources.html" style="color: var(--col-water); text-decoration: none; font-size: 0.9rem; font-weight: 500;">Resources</a>
      <a href="index.html#contact" class="btn btn--primary nav__cta">Get in touch →</a>
    </nav>
  </div>
</header>
```

**Mobile Consideration:**
- Future: hamburger menu at `<600px` breakpoint
- Current: wraps naturally, acceptable for 3 links

### 8.4 Footer Pattern

**Standard Footer (All Pages):**

```html
<footer class="footer" role="contentinfo">
  <div class="container footer__inner">
    <p class="footer__logo">PAUL GRAY <span>Swim Coach</span></p>
    <p class="footer__meta">
      <span>© 2026 Paul Gray</span>
      <a href="[INSTAGRAM_URL]" target="_blank" rel="noopener noreferrer">Instagram</a>
      <a href="[LINKEDIN_URL]" target="_blank" rel="noopener noreferrer">LinkedIn</a>
    </p>
  </div>
</footer>
```

**Links-in-Bio Footer Variant:**
- Omit social links (handled in main content)
- Add "Homepage" and "Links" to `.footer__meta`

### 8.5 Dark Section Pattern (Coach Community Teaser)

**HTML:**

```html
<section class="teaser" id="notify" aria-label="Coach community notice">
  <div class="container">
    <h2 class="teaser__heading">Something for coaches is coming.</h2>
    <p class="teaser__sub">
      A place for coaches, teachers and instructors to share what works
      on deck - discipline, connection, trust, and the craft side of coaching that
      isn't taught in accreditation courses. Not live yet. Interested?
    </p>

    <script async data-uid="[WAITLIST_UID]" src="https://paulgray.kit.com/[WAITLIST_UID]/index.js"></script>

    <p class="teaser__note">No spam. Updates only when there's something ready.</p>
  </div>
</section>
```

**CSS:**

```css
.teaser {
  padding-block: var(--section-v);
  background-color: var(--col-dark-bg);
  color: var(--col-dark-text);
}
@media (prefers-color-scheme: dark) {
  .teaser {
    background-color: #0A2030;
  }
}
```

---

## 9. Content Standards

### 9.1 Credentials Display

**Public-Facing Credentials (as of November 2026):**

Current to list:
- Swim Australia Teacher (SAT) — pending SWIMDeck verification
- Swim Squad Fundamentals (SSF) — certified 30 Sept 2026
- First Aid & CPR — current, childcare setting
- Safeguarding Children in Sport — Sport Integrity Australia
- Anti-Doping Fundamentals — Sport Integrity Australia

Add after completion:
- ASCA Level 1 — workshop 28-29 Nov 2026

**Never list publicly:**
- In-progress credentials before completion
- Expired credentials
- Credentials with unclear completion status

**Format:**

```html
<li class="cred-badge">
  <div>
    <strong class="cred-badge__name">Swim Australia Teacher</strong>
    <span class="cred-badge__issuer">Swim Australia (SAT)</span>
  </div>
</li>
```

### 9.2 Privacy & Data Standards

**Swimmer Data:**
- Public: First names or initials + age group only
- Private files: Warning admonition at top
- Never: Full names, dates of birth, medical data, emergency contacts in shareable contexts
- Col Jones swimmer data: stays in facility systems (SWIMDeck, iClassPro)

**Parent/Client Data:**
- No child-specific data on public forms
- Plain-English privacy policy (future: link in footer)
- Consent checkbox near sign-up forms
- Australian Privacy Principles compliance
- Spam Act compliance (ConvertKit unsubscribe)

**Form Disclaimer Example:**

"By submitting this form, you consent to Paul Gray storing your contact information to respond to your enquiry. Read our [privacy policy](#)."

### 9.3 Copyright & Attribution

**Footer Copyright:**
- "© 2026 Paul Gray" (update year annually)

**Third-Party Content:**
- Swimming records: "Compiled from World Aquatics ratified records and recent competition results, [Month Year]. Records change fast at this level – check worldaquatics.com for anything time-sensitive."
- Research citations: Full APA format in PASS repo, short citation in public content

**Own IP:**
- PASS framework: © Paul Gray, not for redistribution without permission
- Biggest Movers, Fundamentals Check: locked pages in PASS, password-protected

### 9.4 Link Standards

**External Links:**
- Always `target="_blank" rel="noopener noreferrer"` for external URLs
- Descriptive link text ("View on Instagram" not "Click here")
- Icon indicators for external links (future)

**Internal Links:**
- Relative paths (`index.html`, `records.html`)
- Anchor links for on-page navigation (`#contact`, `#notify`)
- Underline on hover for text links

**Social Placeholder Pattern:**
- Use `#` for undefined social URLs with comment: `<!-- UPDATE: swap # for real profile URLs -->`

---

## 10. Implementation Checklist

### 10.1 New Page Checklist

**Before Launch:**
- [ ] Unique page title (50-60 chars)
- [ ] Meta description (150-160 chars)
- [ ] `lang="en-AU"` on `<html>`
- [ ] Theme-color meta tags (light + dark)
- [ ] Viewport meta tag
- [ ] Semantic HTML5 structure
- [ ] Heading hierarchy (one H1)
- [ ] ARIA labels on landmarks
- [ ] Standard nav component
- [ ] Standard footer component
- [ ] All images have descriptive alt text
- [ ] All forms have labels
- [ ] Color contrast passes WCAG AA
- [ ] Keyboard navigation works
- [ ] Focus indicators visible
- [ ] `prefers-reduced-motion` respected
- [ ] Dark mode tested
- [ ] Mobile responsive (test 320px, 480px, 700px, 1200px)
- [ ] External links have `target="_blank" rel="noopener noreferrer"`
- [ ] No console errors
- [ ] Forms submit successfully (or gracefully fail)

### 10.2 Brand Consistency Checklist

**Visual:**
- [ ] Uses design tokens from `:root`
- [ ] Typography matches system (Barlow Condensed headings, Inter body)
- [ ] Colors from defined palette only
- [ ] Spacing uses 0.25rem baseline grid
- [ ] Components match library patterns
- [ ] Buttons use standard classes
- [ ] Cards/badges use standard structure

**Voice & Tone:**
- [ ] Direct, no fluff
- [ ] Australian English spelling
- [ ] Active voice
- [ ] Appropriate for target audience
- [ ] No unsupported claims
- [ ] CTA uses arrow convention (→)

**Technical:**
- [ ] File naming: lowercase, hyphens, descriptive
- [ ] CSS: custom properties, BEM-style naming, mobile-first
- [ ] JS: vanilla, progressively enhanced
- [ ] Images via Cloudinary (or documented exception)
- [ ] Forms via Web3Forms or ConvertKit

### 10.3 Credential Update Checklist

**When a New Credential is Earned:**
1. [ ] Add to master context doc (`6-nov-2026-swimbiz-master-context.md` → update date)
2. [ ] Add to "Public marketing credentials" section
3. [ ] Update credentials section on `index.html`
4. [ ] Update PASS repo guidance file (separate task)
5. [ ] Consider adding to resources page if relevant to audience
6. [ ] Update any waitlist/email templates mentioning credentials
7. [ ] Update LinkedIn, Instagram bio if public-facing

### 10.4 Pre-Deploy Checklist

**Every Site/Page:**
- [ ] All placeholder content replaced (search for "REPLACE", "UPDATE", "TODO", "#")
- [ ] Web3Forms access key added
- [ ] ConvertKit form UIDs added
- [ ] Social media URLs updated (Instagram, LinkedIn)
- [ ] Contact email confirmed (`paul@paulgray.com.au`)
- [ ] SPF DNS record fixed (outstanding issue noted)
- [ ] Test all forms end-to-end
- [ ] Lighthouse audit run (Performance >90, Accessibility 100, Best Practices >90, SEO 100)
- [ ] Cross-browser test (Chrome, Firefox, Safari)
- [ ] Mobile device test (iOS Safari, Android Chrome)
- [ ] Broken link check (all internal and external links)
- [ ] 404 page created (future)
- [ ] Analytics added (future: privacy-first option like Plausible)

---

## Document Control

**Version History:**
- 1.0 (6 Nov 2026): Initial creation from holding site analysis and master context

**Review Schedule:**
- Review quarterly or after major brand/design changes
- Update immediately when design tokens change
- Update when new credentials earned
- Update when sub-brands launch

**Owner:** Paul Gray
**Primary Use:** Reference for Claude Code, designers, developers, future team members
**Related Docs:**
- `6-nov-2026-swimbiz-master-context.md` (business/career context)
- PASS repo: `PaulGrayCo/PerformanceAquaticsSwimmingSystem`
- Style implementation: `style.css`

---

**END OF BRAND & DESIGN BIBLE**
