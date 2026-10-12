# Broken Frame Strategies — website

Four-page static site built with [Astro](https://astro.build): near-black ground, bone and
oxblood panels, ember/spark accents, and a "broken frame" motif drawn from separate line
segments that knock loose as you scroll.

## Run it locally

```bash
npm install
npm run dev      # http://localhost:4321
npm run build    # static site → ./dist
npm run preview  # serve the production build
```

Pushing to `main` deploys to GitHub Pages (`.github/workflows/deploy.yml`) at the custom
domain in `public/CNAME`.

## Structure

```
src/
  layouts/Base.astro            <head>, fonts, footer
  components/
    Nav.astro                   top nav (pass `current` to highlight the page)
    Footer.astro
    Mark.astro                  the broken-frame logo mark (SVG)
    ContactCard.astro           discovery-session madlib form (Web3Forms)
    ContactSection.astro        campfire-photo section wrapping the form
  pages/
    index.astro                 Home — hero, problem, approach, payoff, teasers, contact
    why-narrative.astro         Why Narrative
    our-story.astro             Our Story (Robert's bio + portrait)
    free-consultation.astro     Free Consultation (form)
  styles/global.css             color tokens, broken-frame pieces, animations
public/
  images/                       frame-bonfire.jpg (hero), beach-campfire.jpg (contact)
  robert.jpg                    portrait on Our Story
```

Fonts: **Archivo** (variable, uses the width axis for the condensed headlines) and
**DM Mono**, both self-hosted via `@fontsource` — the page makes no third-party font requests.

Colors live as CSS variables at the top of `src/styles/global.css`.

## The contact form

Wired to **Web3Forms**: submissions POST to their API and arrive by email at the address the
access key was registered with. The key and a mailto fallback address are at the top of
`src/components/ContactCard.astro`. Do a live test submission after any change.

## Motion

Scroll effects (parallax, frame pieces breaking, the "fuse" on Our Story) use CSS
scroll-driven animations. Browsers without support show the static layout; visitors with
reduced motion turned on get no animation.
