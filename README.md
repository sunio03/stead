# Stead — landing page

**Safer, together.** Landing page for Stead, an AI family safety companion built at c0mpiled-17 Seoul (AI for the Aging Population).

Static site, no build step. Open `index.html` or serve the folder:

```
python3 -m http.server 5181
```

- `index.html` — the whole page (HTML, CSS, JS)
- `fluid-glass.js` — FluidGlass footer effect, ported from React Bits to plain JS

## Honesty notes

- All animated demos on this page use **sample data**. Names, numbers and `.example` links are fictional.
- In the Stead prototype, the incoming message is **simulated and labelled**. The AI analysis, safety case, guardian notification and status updates are real.
- Stead never labels a message "safe" and never shows a numeric scam score.

## Links to wire up

CTAs point to `/demo`, `/parent` and `/guardian`, the routes of the Stead app. If this page lives at `public/landing.html` in the Next.js app, or is ported into `src/app/page.tsx`, those links work as they are.
