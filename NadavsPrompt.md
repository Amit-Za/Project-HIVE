# PROJECT HIVE Cinematic Landing Page Dev Guide

Translation of `Nadav's Prompt.txt` into English, restructured as a Markdown specification for building a static GitHub Pages site with only `index.html`, `style.css`, and `script.js`.

---

## 0. Absolute Requirements

- The site must run as a **static GitHub Pages** deployment.
- **No build tools** (no React, bundlers, or compilation steps).
- Repository root must contain exactly three source files:
  - `index.html`
  - `style.css`
  - `script.js`
- All links between these files must work as-is on GitHub Pages.
- Deliver clean, modern HTML/CSS/JS within these files only.

---

## 1. Overall Structure

- Build a landing page consisting of **five vertical screens**, each 100% viewport height (`100vh`):
  1. HERO
  2. WHY
  3. HOW
  4. WHAT
  5. CONTACT
- Scrolling behavior:
  - Full-page scroll experience (story/reel style).
  - One scroll wheel movement (or swipe) moves to the next/previous screen.
  - Implement with CSS `scroll-snap` + `100vh` sections, optionally reinforced with light JS.
  - No half screens; each scroll snaps to a full screen.

---

## 2. Visual Language

### Color Palette (Bee / Dark Mode)
- Background: deep black (`#000000`).
- Primary text: white (`#FFFFFF`).
- Accent yellow (hive/bee tone): `#F4D74A` for highlights, CTAs, indicators.

### Typography
- Use a modern Google Font such as `Inter` or `Space Grotesk`.
- Add the `<link>` in `index.html`, with `sans-serif` as fallback.

### Style Guidelines
- Minimalist, futuristic, premium tech aesthetic.
- Avoid harsh gradients or unnecessary ornamentation.
- Allowed: thin lines, subtle particles, faint honeycomb/data-flow patterns.

### Dynamic Background
- Every screen shares a black background with gentle animated elements (lines, dots, particles).
- Animation must be slow, soft, and unobtrusive (CSS animations or simple JS).

---

## 3. Screen 1 – HERO

### Layout
- Content centered vertically and horizontally using flex column layout.
- Small textual PROJECT HIVE logo in top-left corner (yellow text).

### Copy
- Heading: “Ready to be part of the future?”
- Subheading: “Something new is coming to your city.”
- Single CTA button: “Enter the Hive”
- No extra scroll hints; this button is the only call-to-action.

### CTA Behavior
- On click, smooth-scroll to the WHY screen (`scrollIntoView({ behavior: 'smooth' })`).

### Typography & Button Styling
- Heading: 54–72px (desktop), semi-bold, white.
- Subheading: 20–26px, regular/light, light gray (`#E9E9E9`).
- Button: yellow background `#F4D74A`, black text, 8–12px radius, ~14px x 32px padding, subtle box-shadow.
- Hover: `transform: scale(1.03)`, lightened yellow, `transition: 0.2s ease-out`.

### Intro Animations
- On load:
  - Black background appears immediately.
  - Heading fades in from opacity 0 with slight upward motion after ~200ms.
  - Subheading follows soon after with same effect.
  - Button fades in last.
- Optional hover effect on heading/subheading: slight scale (1.02) with quick transition.

---

## 4. Screen 2 – WHY

### Copy (full text)
```
Cities are alive.

They grow, shift, breathe,
yet the systems guiding them haven’t evolved with the rhythm.

Traffic isn’t a problem of cars.
It’s a lack of flow.
A gap in understanding how a city truly moves.

We believe cities deserve movement that finally makes sense.

This is why we started PROJECT HIVE.
```

### Layout & Styling
- Text block positioned left-center (vertical center, ~10vw left margin).
- “Cities are alive.” slightly larger (28–32px). Remaining lines 22–26px.
- Use white for emphasis lines, light gray (`#D9D9D9`) for supporting lines.

### Animation & Hover
- Reveal sequence:
  1. “Cities are alive.”
  2. Next two lines.
  3. “Traffic isn’t a problem…” block.
  4. “We believe cities deserve…”
  5. “This is why we started PROJECT HIVE.”
- Wrap each line in spans for hover effects (`transform: scale(1.03)`, increased opacity/white).

### Background
- Maintain black base.
- Add subtle breathing dots or soft circles with slow fade in/out to imply a living city.

---

## 5. Screen 3 – HOW

### Copy
```
We’re giving your city something it never had:
a brain.

A layer that senses how movement forms,
anticipates what’s coming next,
and adjusts the city’s flow before anyone feels the slowdown.

Nothing to install.
Nothing to maintain.
Just intelligence working quietly all across the city.
```

### Design Notes
- “We’re giving your city…” standard line.
- “a brain.” isolated, larger, bold, pure white.
- Paragraph lines 22–24px.
- “Nothing to install…” lines stacked, slightly emphasized.

### Animation
- Intro sequence:
  1. First line fades in.
  2. “a brain.” scales from 0.95 → 1 with fade.
  3. Remaining text fades in upward.

### Background
- Faint honeycomb pattern (5–8% opacity) with subtle glow hints to suggest neural network.

---

## 6. Screen 4 – WHAT

### Copy
```
PROJECT HIVE reshapes how an entire city moves.

No hardware. No installations.
A citywide layer of intelligence that improves flow, reduces stops, and keeps movement alive without touching a single traffic light.

It works at scale.
It’s faster to deploy.
And it costs a fraction of anything the market has seen before.

And the longer it runs, the smarter it becomes.
Your city evolves week by week.

Cities feel the change right away.
Engineers see the results.
Drivers sense the difference without even knowing why.

It feels like magic.
But it’s real.

Want to hear how we do it?
Contact us for more.
```

### Styling & Hierarchy
- Lead sentence as headline.
- “No hardware. No installations.” bold/bright.
- Present “It works at scale… It’s faster… costs a fraction…” as highlighted lines or short bullets.
- Emphasize “And the longer it runs…” to underscore compounding intelligence.
- Final block (“Cities feel the change…”) acts as emotional close.

### Animation Order
1. Headline
2. “No hardware. No installations.”
3. Citywide layer paragraph
4. Deployment benefit lines
5. “And the longer it runs…”
6. “Cities feel the change…”
7. Ending punch: “It feels like magic. But it’s real.” then “Want to hear how we do it? Contact us for more.”

### Background
- Add gentle moving lines representing data/traffic flows (slow, single-direction motion).

---

## 7. Screen 5 – CONTACT

### Copy
```
Let’s talk.
If you’re responsible for how your city moves,
we’d love to show you what we’re building.
```

Form fields:
- Name (required)
- Role
- Municipality (required)
- Email (required, validate format)
- Phone

CTA Button: “Get in touch”

Small note below: “For early access cities only.”

### Design
- “Let’s talk.” as large headline.
- Two-line body text beneath.
- Centered minimalist form:
  - Transparent inputs, white/gray bottom border.
  - White text, gray placeholders.
- Button matches HERO CTA (yellow background, black text, hover scale).

### Validation
- Required fields for Name, Email, Municipality.
- Basic email regex check.
- Display inline error text or simple alert.

---

## 8. Transitions & Effects

- Use CSS `scroll-snap` (or equivalent) for screen snapping.
- Set `scroll-behavior: smooth` globally; supplement with JS as needed.
- Trigger fade-in animations when each section enters view (scroll or Intersection Observer).
- Key typography hover interactions (desktop):
  - `transform: scale(1.02–1.03)`
  - `transition: 0.15–0.2s`

---

## 9. File Layout (GitHub Pages Ready)

1. `index.html`
   - Contains full HTML structure for all five screens.
   - Includes:
     - `<link rel="stylesheet" href="style.css">`
     - `<script src="script.js"></script>` just before closing `</body>`.
2. `style.css`
   - Global reset, typography, colors, layout.
   - Styles for screens, text, buttons, background animations.
3. `script.js`
   - Smooth scroll logic for CTA.
   - Scroll/Intersection Observer animations.
   - Contact form validation.

All files must live at the repository root so GitHub Pages can serve `index.html` without additional configuration.

---

## Deliverable

Provide full, production-ready code for `index.html`, `style.css`, and `script.js` implementing every detail above so the site feels like a futuristic cinematic trailer for PROJECT HIVE and runs directly on GitHub Pages with zero build steps.

