# toshangoswami.github.io

Long-lived personal site, not tied to one application. This is my long-term portfolio.
Plain HTML + CSS, no frameworks, no build step, deployed by GitHub Pages from `main`.

## Core line

> I put sensors on physical things nobody is measuring well, and build the software
> that makes sense of them.

If a section doesn't support this, it probably doesn't belong.

## Ground rules

- **I write all the copy; you build the structure.** Markup, CSS, and layout are yours.
  Prose, project text, results, and the bio are mine.
- **Never invent facts.** No invented numbers, results, metrics, dates, or claims.
  If you don't have it from me, leave a visible `TODO:` in the page where it goes and
  tell me what's missing. A `TODO:` is correct. A plausible guess is not.
- **Don't write marketing copy or adjectives.** State what a thing is and what it does.
  If a sentence survives deleting its adjectives, delete them.
- **One step per task.** Change one section, stop, tell me how to preview it, and wait
  for me to commit. Don't start the next step. If you spot something unrelated that's
  broken, tell me instead of fixing it.

## Voice

- First person.
- "engineering student at the University of Michigan". Don't name a major.
- Short sentences. Concrete nouns.

## Structure

Homepage is one scrolling page, in this order:

1. Hero — the polaroid flipbook, with my name and the core line beside it
2. Featured project cards — directly below the hero
3. Compact all-projects list
4. Now log
5. About
6. Footer

No video in the hero. Video belongs in featured card covers.

Resume link in the nav and in About.

Each featured project gets its own page at `/projects/<slug>/` using one shared
template. "No build step" means no bundler and no framework, not one single file —
multiple pages, each self-contained HTML, sharing one stylesheet.

### Featured cards

Three to four. Three live now:

- Airframe AE
- WindMesh
- Badminton Tracker

A fourth comes later (robot arm). Don't render an empty slot for it.
RC Car stays in the all-projects list only.

Cards carry three fields: media, what I built, one result.
Project pages carry five: problem, what I built, media, result, what broke.

### Media

A featured card cover is either an image or a short muted looping MP4. The hero
flipbook is hand-drawn SVG, not video.

- Video: `<video muted loop playsinline autoplay preload="metadata" poster="...">`,
  with the poster image as the fallback.
- Keep media small — under 5MB per video (GitHub rejects files over 100MB).
- Always set `width`/`height` or `aspect-ratio` so nothing shifts on load.
- Lazy-load anything below the fold.

## Design system

Tokens live in one place, in `:root` in `assets/css/site.css`. Don't hardcode colors
or sizes in markup.

**Type** — two families, from Google Fonts.

- Display (name, section headings): Instrument Serif 400
- Everything else: Inter 400/500
- Metadata (years, tags) is small Inter with letterspacing, not a third font
- Scale: 13 / 15 / 18 / 24 / 34px; display `clamp(2.6rem, 6vw, 4.5rem)`

**Color** — warm paper, accent pulled from the hand-drawn city artwork.

    --paper        #f4f1ea
    --ink          #1b1a17
    --ink-soft     rgba(27,26,23,.56)
    --hairline     rgba(27,26,23,.12)
    --accent       #2e3f5c
    --accent-warm  #c06b3e   /* used once, sparingly */

Redefine only these tokens under `prefers-color-scheme: dark`.

**Layout** — left-aligned. 1040px max page width, 680px for prose. 8px spacing base.
96px between sections, 64px on mobile. Hairlines carry the structure; no boxes,
borders, or shadows except on the featured cards and the polaroid.

**Motion** — the hero flipbook flip, card cover videos, and row hover fades.
Nothing else moves.

## Performance and accessibility

- No frameworks and no CDN JavaScript.
- Under ~150KB per page, excluding media.
- Must work on mobile and load fast. Check 375 / 768 / 1280.
- Everything reachable by keyboard, with visible focus.
- Real contrast. No blurred text.

## Attribution

The design started as a rebuild of matthewyu.dev. Keep a small credit line in the
footer until the design pass lands, then remove it in the same commit that makes the
design its own.

## Deploy

Push to `main`. No build step. Work happens on branches.