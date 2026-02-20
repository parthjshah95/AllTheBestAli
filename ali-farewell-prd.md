# PRD: Ali Moeeny Farewell Website
**Domain:** alimoeeny.com  
**Purpose:** A one-page farewell tribute for Ali Moeeny, built as a surprise gift from his team at Insito Health as he departs to start his own company.

---

## Background & Context

Ali used the Harry Potter books to learn English when he first moved to the United States. HP has also been a frequent topic of conversation between Ali and the team recently. The site should treat this as a meaningful personal thread — not just a fun theme — and weave it into the tribute genuinely.

Ali is the rightmost person in the group photo on the Insito Health company page. This photo should be fetched and used on the page.

---

## Goal

Build a beautiful, single-page static HTML website (no backend needed) that:
- Celebrates Ali's contributions to the team
- Wishes him well on his startup journey
- Uses Harry Potter as an emotionally resonant theme
- Feels personal, warm, and high-quality — not generic

---

## Design & Theme

**Aesthetic:** Wizarding world — dark parchment background, gold/amber accents, candle/star motifs. Think the Great Hall or Dumbledore's office. Not cartoon-y; more elegant and cinematic.

**Fonts:** 
- A serif/display font for headings (something like IM Fell English or Cinzel from Google Fonts)
- Clean readable body font (Lora or similar)

**Color palette:**
- Background: deep navy or dark parchment (#1a1a2e or #2c1810)
- Gold accents: #c9a84c
- Text: warm off-white (#f5e6c8)

**Motifs to incorporate:**
- Floating candles or stars (CSS animation)
- A subtle Hogwarts crest watermark or decorative dividers
- Wax seal or scroll-style section breaks

---

## Animations (Detailed Spec)

All animations should be implemented in vanilla JS + CSS — no animation libraries. Performance matters; use `requestAnimationFrame` for canvas-based animations and `will-change: transform` on CSS-animated elements. Animations should not cause layout thrashing or block scrolling.

### 1. Floating Candles (Global / Hero Background)
- Render 12–16 candle SVGs floating upward slowly across the full page background
- Each candle has a small animated flame (flickering via CSS `@keyframes` with subtle scale + opacity oscillation)
- Candles drift upward at different speeds and horizontal drift, looping infinitely
- A thin wisp of "smoke" rises from each flame (a faint, wavy CSS animation)
- Position: fixed in background, behind all content, low opacity (~0.35) so they don't overpower the text

### 2. Flying Owls
- 2–3 owls fly across the screen at different times and heights
- Implement as SVG sprites or CSS-drawn owls with wing-flap animation (alternating wing up/down via CSS keyframes)
- Owls fly in from off-screen left or right, traverse the full width, and disappear off the other side
- Each owl flies at a slightly different altitude and speed
- They should appear occasionally (not constantly) — stagger their entry with delays of 8–15 seconds apart
- One owl could carry a small envelope/letter in its talons (a nod to Hedwig delivering mail)
- Owls should have a slight vertical bob as they fly (sine wave motion via JS or CSS)

### 3. Graduation Scene — "The Ceremony" (Hero or Farewell Section)
This is the hero animation. Triggered either on page load or when the user scrolls to the farewell section.

- **Use the provided team photo (`team-photo.png`) to create a recognizable SVG silhouette of Ali** — he is the rightmost person: curly dark hair, beard, medium build. Trace his outline into a clean SVG silhouette that is distinctly *him*, not a generic wizard figure. Add a graduation cap on top of his head and a flowing wizard robe.
- The Ali silhouette walks across the screen from left to right using a CSS walking cycle (slight bob, arm swing)
- As it walks, it receives a glowing scroll (diploma) that appears with a sparkle effect
- The figure then throws its cap into the air — cap tumbles upward with CSS rotation, then falls back
- Golden sparks/particles burst from the cap toss moment
- Beneath the figure, text fades in: *"Hogwarts Class of Insito"*
- The figure then continues walking off-screen to the right, into the unknown (toward the startup)
- Style: simple and elegant — silhouette art, not a game character. The Ali-specific silhouette is what makes this special.
- Implementation: SVG animation or Canvas 2D, whichever produces smoother results

### 4. Scroll-Triggered Spell Reveals (Contributions Section)
- Each spell entry in the "Spells He Cast" section is hidden initially
- As the user scrolls each spell into view, it animates in as if being written by an invisible quill:
  - The spell name appears letter by letter (typewriter effect) in gold
  - A small wand-flick particle burst accompanies the reveal
  - The description fades in underneath after the spell name finishes typing
- Use `IntersectionObserver` to trigger each spell independently as it enters the viewport

### 5. Marauder's Map Ink Reveal (His Story Section)
- The "His Story" section text appears as if being revealed by invisible ink on parchment
- On scroll into view: text starts fully invisible, then a slow ink-spread effect reveals it left to right
- Implement via a CSS `clip-path` animation or SVG mask that sweeps across the text block
- Optionally add a faint parchment texture to the section background

### 6. Stars / Night Sky (Ambient)
- Small twinkling stars scattered in the background (complement the candles)
- Implemented as tiny dots that pulse opacity on staggered timers
- Should feel like looking up at the Hogwarts ceiling in the Great Hall

---

## Page Structure

### 1. Hero Section
- Heading: **"Mischief Managed."**
- Subheading: something like *"But the magic you left behind? That stays."*
- Subtle animated floating candles or stars in the background

### 2. His Story — "The Boy Who Read"
This is the most personal and important section.

Write a short, warm paragraph acknowledging that Ali came to the US and learned English through the Harry Potter books. Frame his startup journey as the next chapter — he arrived in a new world with a book as his guide, and now he's writing his own story. This section should feel heartfelt, not cheesy.

### 3. Team Photo Section — "The Order"
- Title: **"The Order of Insito"** (riff on Order of the Phoenix)
- The team photo has been provided directly (see `team-photo.png` in the project assets). It shows 4 people standing together in front of a brick wall. **Ali is the rightmost person** — curly dark hair, beard, black t-shirt.
- Display the photo in a styled frame — consider a aged portrait frame look, or a circular vignette with a gold border, to fit the wizarding aesthetic
- Remove or crop out the "Our Team" bubble graphic and the colorful blob shapes from the original if possible (or just crop the photo tightly to the four people)
- Caption: something like *"Ali, rightmost, as always — leading from the edge."*

### 4. Contributions Section — "Chapters Written"
- Title: **"Chapters Written"** or **"The Spells He Cast"**
- A few short tribute lines about his contributions (write these as placeholders since the gifter will want to customize — use `[PLACEHOLDER]` tags for specific achievements)
- Style as a scroll or list of "spells" with made-up HP-style spell names that correspond to his real contributions
  - e.g., *"Buildulus Rapidus"* — shipped features faster than anyone thought possible
  - *"Mentorus Maxima"* — elevated everyone around him
  - Make up 4–5 spell names with placeholder descriptions

### 5. Farewell Message — "The Next Chapter"
- Title: **"The Next Chapter"**
- A warm closing paragraph wishing Ali well on his startup
- Frame it as: he graduated from Hogwarts (Insito), and now the real adventure begins
- End with something like: *"We solemnly swear we are rooting for you."*

### 6. Footer
- Small text: *"With love, the Insito Health team"*
- The domain alimoeeny.com — now his, a blank canvas for the story ahead
- Optionally a small HP-style wax seal icon

---

## Technical Requirements

- **Single HTML file** — all CSS and JS inline or embedded. No build step. No dependencies except Google Fonts CDN.
- **Fully static** — can be dropped into any web host (Netlify, GitHub Pages, etc.)
- **Responsive** — looks good on mobile and desktop
- **Group photo:** The team photo is provided as `team-photo.png` in the project assets. Use it directly — do not fetch from the website. Crop tightly to the four people if possible to remove the bubble graphic and colored blob shapes from the original.
- **Ali silhouette:** Derive an SVG silhouette of Ali (rightmost in the photo — curly hair, beard, black t-shirt) for the graduation animation. It should be recognizably *him* in outline.
- **Animations:** See the detailed Animations section above. All implemented in vanilla JS + CSS only. Use `IntersectionObserver` for scroll-triggered effects. Use `requestAnimationFrame` for canvas/JS animations. No animation libraries (no GSAP, no Anime.js). Animations must not block scrolling or cause jank.
- **No placeholder lorem ipsum** — all text should be real, written in the HP theme, with `[CUSTOMIZE: ...]` markers only for facts the gifter needs to fill in (e.g., specific project names, achievements)

---

## Deliverable

A single file: `index.html`  
Ready to upload to the root of alimoeeny.com hosting.

---

## Handwritten Card Message (to accompany the gift)

The gifter is also giving Ali a Harry Potter-themed handwritten card. The card will be used to hand Ali the login credentials for the domain registrar account. The tone should be warm, slightly whimsical, and tie into the website.

**Suggested card message:**

> *Ali —*
>
> *You once crossed an ocean with Harry Potter as your guide. Now it's your turn to write the adventure.*
>
> *Welcome to alimoeeny.com — your blank page, your story.*
>
> *To get started:*  
> *🔐 Registrar: [NAME]* 
> *📧 Login: [EMAIL]*  
> *🗝 Password: [PASSWORD]*
>
> *We solemnly swear we are rooting for you.*
>
> *— [Your name & the team]*

---

## Notes for Claude Code

- Keep the writing quality high. This is a personal, heartfelt gift — not a template.
- The HP theme should feel earned and specific to Ali's story, not just aesthetic decoration.
- When in doubt, lean warmer and more personal rather than more elaborate.
- Prioritize the "His Story" section — that's the emotional core of the page.
