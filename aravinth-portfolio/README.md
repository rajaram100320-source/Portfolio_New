# Aravinth Kumar M — The Engineering System

Interactive engineering portfolio. No build step, no dependencies to install.

## Two builds

- `index.html` + `assets/` — normal build. Drop the whole folder into any static
  host (Vercel, Netlify, GitHub Pages, S3). On Vercel: drag the folder in, or
  `vercel deploy` from inside it. No framework config needed.
- `single-file/index.html` — everything inlined, including the artwork. One file,
  works offline, can be emailed or opened straight from disk.

Three libraries load from cdnjs at runtime: three.js r128, GSAP 3.12.5 and
ScrollTrigger. Fonts come from Google Fonts (Orbitron, Inter, JetBrains Mono).

## Editing your content

All facts live in one object, `CONTENT`, near the top of the second `<script>`:
identity, nav, modules, projects, skills, matrix, timeline, experience,
achievements, contact. Change a value there and it updates everywhere — cards,
the project overlay, the skills graph, the timeline panel.

## The hero scene

The command-deck artwork is `assets/backdrop.webp`. Everything live in the hero
is pinned to a point inside that image through the `PIN` object:

    PIN.globe      centre of the WebGL globe, as a fraction of the image
    PIN.globeR     globe radius, as a fraction of image width
    PIN.engineer   [x, y, width, height] of the engineer cutout
    PIN.chips      the nine holographic module positions, in image order

`layoutStage()` works out where the image actually lands on screen and places
each element accordingly, so the composition holds at any window size. If you
replace the backdrop, re-measure those fractions and nothing else changes.

The engineer (`assets/engineer.webp`) is a separate transparent layer drawn
above the canvas — that is what keeps him in front of the rotating globe.

## Project artwork

`assets/project-1.webp` … `project-3.webp`, in the same order as
`CONTENT.projects`. Swap in real screenshots at roughly 300x308 and they will
drop straight into the cards.

## Accessibility and performance

Respects `prefers-reduced-motion`, traps focus in the project overlay, closes on
Escape, keeps visible keyboard focus, and drops particle counts and pixel ratio
on phones. Interface sound is off until you turn it on.
