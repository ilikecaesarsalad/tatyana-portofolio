# Tatyana Faradilla R. — personal portfolio

A small, hand-written static website. No build step, no frameworks, no backend.
Open `index.html` in a browser and it runs.

---

## Files

```
tatiporto/
├── index.html              all the text and structure — edit this most
├── css/style.css           all the styling (colours and fonts at the top)
├── css/scenes.css          where the Shanghai artwork sits, and the links between sections
├── css/projects.css        project rows + the live project viewer
├── js/main.js              menu, scroll reveals, project filter, copy button, timeline
├── js/projects.js          the live project viewer
├── assets/
│   ├── fonts/              Noisy Walk, Lemon Milk, Instrument Serif, Pinyon Script, Karla (+ licences)
│   ├── scenes/             the Shanghai artwork, plain SVG (open in Figma/Illustrator)
│   └── images/
│       ├── placeholder-*.svg      temporary images — replace with your own
│       └── city-window.svg        site icon
└── README.md
```

## How the code is written

- **No comments.** The code carries no comments at all; this README is the
  documentation. That includes the three project apps in `projects/`.
- **Every class ends in `_tatyana`**, in the HTML, the CSS and the JavaScript:
  `hero_tatyana`, `btn--solid_tatyana`, `is-open_tatyana` and so on. When you add
  a class, add the suffix in all three places, or the style or behaviour won't
  connect. IDs (`#nav`, `#contact`...) and `data-` attributes have no suffix.
- **The three project apps in `projects/` keep their own class names.** They are
  separate websites shown inside the viewer, not part of the portfolio's code;
  only their comments were removed.

## Running it on Windows

Double-clicking `index.html` works for everything except the "copy email" button,
which browsers only allow on a real address (`http://` or `https://`).

For editing, VS Code with the **Live Server** extension is easiest: right-click
`index.html` → *Open with Live Server*. The page reloads as you save.

---

## What to edit

Sections in `index.html` are in page order. Each one has an `id` you can search
for: `#top`, `#services`, `#skills`, `#projects`, `#experience`, `#education`,
`#about`, `#contact`.

| What you want to change | Where |
|---|---|
| Your introduction, role line, corner notes | `SECTION 1 — INTRODUCTION` |
| The five things you do | `SECTION 2 — WHAT I DO` |
| Skills (just `<li>` items, add or remove freely) | `SECTION 3 — HARD SKILLS` |
| Projects | `SECTION 4 — PROJECTS` |
| Experience (timeline) | `SECTION 5 — EXPERIENCE` |
| Education and languages | `SECTION 5b — EDUCATION & LANGUAGES` |
| How you work | `SECTION 6 — HOW I WORK` |
| Email, WhatsApp, iMessage | `SECTION 7 — CONTACT` |

### Projects (they open live)

Each project lives in its own folder and runs inside the page:

```
projects/
├── hotel-sriwidjaja/   index.html (guest site) + admin.html (admin panel)
├── egg-timer/          index.html
└── tourify/            index.html
```

These files are the original offline builds, unchanged. Clicking a card opens
the real project in a full-screen viewer (`js/projects.js`, `css/projects.css`)
that grows out of the card. "Back to portfolio" (or Esc while the bar has focus)
shrinks it back. Closing removes the project, so its sound and timers stop.

- Ctrl/Cmd-click or middle-click a card still opens the project in a new tab.
- Links like `index.html#project/tourify` open a project directly.
- Hotel Sriwidjaja has two tabs in the viewer. Both pages share browser storage,
  so a booking made on the guest site appears in the admin panel.

### Adding a project

1. Put the project in `projects/<name>/`. Its `index.html` must work on its own.
2. Copy one `<article class="work_tatyana">…</article>` block inside `<div class="works_tatyana">`.
3. Change `data-project` (short id), `data-category` (one or more of `web`, `app`,
   `uiux`, `interior`, `video`, separated by spaces), every `href` into `projects/`,
   the preview images, the texts and the facts (Purpose, Key features, Built with,
   My contribution). The element with `data-origin` is where the viewer grows from.
4. Links with `data-view` become the viewer's tabs; `data-label` is the tab name.
   One `data-view` link means no tabs.
5. `<template class="project__tips_tatyana">` is the "How to try it" list in the viewer.

Filter buttons with no matching project hide themselves and come back once you
add one.

Preview images are real screenshots of each project (`shot-*.jpg`), shown
inside CSS browser and phone frames. `hotel_sriwidjaja.png`,
`eggtimer_d.png` and `school_team_project.png` are no longer used and can be
deleted.

### Adding an experience entry

Copy one `<li class="tl_tatyana">…</li>` block inside `<ol class="timeline_tatyana">` (most recent
first) and fill in the dates, role, organization and description. The glowing
line and the dots light up on their own as you scroll.

### Contact

Each contact method is one `<li class="reach__item_tatyana">` with a link and a Copy
button (`data-copy` is what gets copied).

- WhatsApp: `https://wa.me/6287815055573`, the number in international format
  (country code, no `+`, no leading `0`).
- iMessage: an `sms:` link, which opens Messages on iPhone, iPad and Mac. On other
  devices the click copies the address instead and says why.

---

## Replacing the images

All placeholders live in `assets/images/`. Put your own file in the same folder
and point the `src` at it. Suggested sizes:

| Placeholder | Used for | Good size |
|---|---|---|
| `profilepicture.jpg` | hero photo, shown in the heart frame | square, about 1024 × 1024 px, face in the upper middle |
| `placeholder-workspace.svg` | "How I work" photo | about 1600 × 1000 px |
| `placeholder-project-01…06.svg` | project thumbnails | about 1280 × 960 px (4:3) |

Example:

```html
<img src="assets/images/portrait.jpg" alt="Tatyana at her desk" width="900" height="1150">
```

Keep files under roughly 400 KB each so the page stays fast. Update the `alt` text
to describe the picture — it matters for screen readers and for search engines.

---

## Colours and fonts

Both are at the top of `css/style.css` in one `:root` block. `--amber` is kept
as another name for `--cyan` because the project viewer still uses it.

```css
--night-1: #140B3E;   /* page base */
--cyan:    #45E6F5;   /* first accent: links, labels, focus */
--pink:    #FF5C9D;   /* second accent: main buttons, the neon name */
--ink:     #F5F3FF;   /* main text */
```

Fonts are bundled, so the site works offline and looks the same on every computer:

| Font | Used for |
|---|---|
| **Noisy Walk** | all the big text: the name, section titles, "LET'S WORK", project titles, services, job titles, the university, the "How I work" headings, the phone menu |
| **Lemon Milk** | all the smaller text: descriptions, buttons, tags, dates, navigation |
| **Instrument Serif** | the small italic labels, the "Tatyana F." logo, email and phone numbers |
| **Pinyon Script** | the neon "Faradilla R." and "together" |
| **Karla** | fallback only |

- **Noisy Walk has letters only** (capitals, no digits or punctuation). The
  `& ' , /` in headings come from Lemon Milk, scaled to match
  ("Noisy Walk Marks" in `css/style.css`).
- **Noisy Walk licence - check before publishing.** The font file says
  "Copyright (c) 2020 by Vladimir Nikolic. All rights reserved." and nothing
  about free use, and it came without a licence file. Check the terms on the
  page you downloaded it from; if it is not free for your use, swap it out in
  the `--font-big` line of `css/style.css`.
- Instrument Serif, Pinyon Script and Karla are open source (SIL Open Font
  License); the licence files are in `assets/fonts/`.
- **Lemon Milk** (by Marsnev) is free for personal and educational use, which
  covers a student portfolio. Commercial use asks for a donation - see
  `assets/fonts/LemonMilk-READ_ME.txt`. Keep that file with the fonts.
- Both Noisy Walk and Lemon Milk are **capitals only**, so text shows in
  capitals; the words in `index.html` are still written normally.
- **Sizes:** capitals look bigger than lowercase at the same size, so both fonts
  are scaled down to match. The knobs are at the top of `css/style.css`:
  `--big-k` (big text), `--sans-k` (short small text) and `--body-k` (descriptions).
- **Want the long descriptions back in normal lowercase?** At the top of
  `css/style.css`, replace the five `--font-body` / `--body-*` lines with:

  ```css
  --font-body: "Karla", "Segoe UI", system-ui, sans-serif;
  --body-k: 1; --body-track: normal; --body-weight: 400; --body-leading: 1.62;
  ```
  Buttons, tags, dates and navigation stay in Lemon Milk.

---

## Putting it online

**GitHub Pages** — create a repository, upload this whole folder, then
Settings → Pages → Branch: `main`, Folder: `/root`. Your site appears at
`https://your-username.github.io/repository-name/`.

**Netlify** — go to app.netlify.com, drag the folder onto the page. Done.

Before publishing, update the `og:` tags in `<head>` so link previews show your
own photo and description.

---

## Notes

- Experience, education and languages come from the resume, word for word.
- **Check before publishing:** the "My contribution" lines for Egg Timer and
  Tourify are not in the resume or the project files. (They used to carry a
  `CONFIRM` comment in `index.html`; that went with all the other comments.)
- The site is responsive down to small phones, keyboard-navigable, and respects
  the system "reduce motion" setting.
- No analytics, no cookies, no trackers.

---

## The Shanghai scenes

Each section is one frame of a night in Shanghai. The artwork is decorative
(`aria-hidden`) and sits only in the margins and the padding, never behind text.

| Section | Scene | Carries on into the next with |
|---|---|---|
| Introduction | skyline and river: Oriental Pearl, Jin Mao, SWFC, Shanghai Tower | a plane heading on |
| What I do | towers at the screen edges | a neon light trail |
| Skills | lit facades at the edges | one glowing window |
| Projects | a small skyline inside every preview window | reflection streaks |
| Experience | the timeline is a metro line, dates as station names | the line bending away |
| Education | distant skyline, wide sky | the horizon line |
| How I work | the horizon reflected in water; illustration beside the text | ripples |
| Interlude | a collage with a key-fret border, **no text** | a neon diamond |
| Contact | a road running out to the skyline | the road |
| Finale | the full panorama with the Nanpu-style bridge, **no text** | - |

- **Editing the art:** every file in `assets/scenes/` is plain SVG. Open it in
  Figma or Illustrator, change it, save it under the same name.
- **Where things sit:** `css/scenes.css`, grouped by section in page order.
- **Removing the two text-free parts:** delete the `<div class="interlude_tatyana">` or
  `<div class="finale_tatyana">` block in `index.html`. Nothing else depends on them.
- **Motion (kept simple):** the name and intro rise in once; each section
  fades up as you reach it; the heart frame beats softly; the plane glides
  across its lane and loops; the metro line lights up as you scroll. With the
  system "reduce motion" setting on, nothing moves and everything shows at once.
- **The heart frame** is `assets/scenes/heart-frame.svg` (the outline) plus the
  same heart shape used as a mask on the photo in `css/style.css`. A square photo
  with the face in the upper middle fits best.
- **Screen sizes:** checked from 320 px phones to 2560 px monitors, including
  landscape phones and tablets.
  - Phones: the edge towers are hidden so the text keeps the full width, the
    skylines keep the Pearl-to-Shanghai-Tower cluster in view, the collage
    becomes two columns, and every button is at least 44 px tall to tap.
  - Large monitors: the wide skylines (2560 px of art) stop growing at their
    natural height and show more of the city at the sides instead, so they
    never rise into the text.
  - The plane is placed in the skyline's own scale, so it always flies above the
    towers, between the intro text and the portrait.

**Email and phone numbers** stay in Instrument Serif rather than capitals, so
they are easy to read and copy exactly.
