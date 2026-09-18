# Broken Frame Strategies — website

Dark, cinematic, type-forward one-page site built with [Astro](https://astro.build).
Matches the approved design comp: plum base, sunset-fire accents, broken-frame motif.

## Run it locally

```bash
npm install
npm run dev      # http://localhost:4321
```

```bash
npm run build    # outputs static site to ./dist
npm run preview  # preview the production build
```

Deploy the `dist/` folder to any static host (Netlify, Vercel, Cloudflare Pages, S3, etc.).
No server required. Set your production domain in `astro.config.mjs` (`site:`) before deploying.

## Structure

```
src/
  layouts/Base.astro        shared <head>, fonts, scroll-reveal
  components/
    Nav.astro               fixed nav + mobile menu
    Hero.astro              "Ignite your brand story" + sunset panel
    Problem.astro           01 — The Real Problem
    Approach.astro          02 — The Approach
    Payoff.astro            03 — The Payoff (staggered cards)
    About.astro             04 — About (your bio)
    Contact.astro           discovery-session madlib form
    Footer.astro
  pages/index.astro         assembles the page
  styles/global.css         design tokens (colors, type, spacing)
public/
  fonts/                    self-hosted Fraunces + Inter (no external calls)
  favicon.svg
```

Fonts: **Fraunces** (display serif) + **Inter** (body). Both self-hosted — the page
makes zero third-party requests, so it loads fast and stays private.

## Before you go live — 4 things that need YOU

1. **About page, one line.** `src/components/About.astro` has a placeholder marked
   with a dashed underline: *"the craft of story structure itself."* Replace it with
   your real answer — the specific side obsession (screenwriting? myth? story theory?).
   Search the file for `data-needs-input`.

2. **The contact form — one value.** The form is wired to **Web3Forms** (free, no
   dashboard, no third-party script on the page). To turn it on:
   - Go to https://web3forms.com, enter the email where you want submissions to land,
     and they'll email you an **Access Key** (a UUID).
   - Paste it into `ACCESS_KEY` at the top of `src/components/Contact.astro`.

   That's the whole setup. Until a key is set, the form gracefully falls back to opening
   a pre-filled email to `FALLBACK_EMAIL` (also at the top of that file — make it a real
   inbox). Submit, error, spam-honeypot, and validation states are all built and tested.
   **Do a live test submission before the DNS switch** (per the spec). Free tier is 250
   submissions/month; swapping to Formspree/Basin later is a one-line change.

3. **Your photo.** `About.astro` has a "Portrait" placeholder frame. Drop a real image
   into `public/` and swap the `.portrait` div for an `<img>`.

4. **Real proof (optional but recommended).** The comp has no logos or results, but one
   line with a concrete outcome would carry more weight than anything else on the page.

## Notes

- Dark theme only, to match the comp. Colors are CSS variables in `global.css`, so a
  light theme can be layered later if you want it.
- Accessible: keyboard focus states, reduced-motion support, semantic landmarks, labelled
  form fields.
