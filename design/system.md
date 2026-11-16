# AG Consulting presentation — design system

Synced from `src/styles/global.css`, the only design source in this project (there are no
token files, no Tailwind config and no component library). Every value below is quoted from
that stylesheet; nothing here is invented.

## Color

| Token | Value | Usage | Source |
| --- | --- | --- | --- |
| `--ink` | `#202124` | Primary text on light, background of dark slides | `src/styles/global.css:16` |
| `--muted` | `#66686b` | Eyebrow labels, secondary text on light | `src/styles/global.css:17` |
| `--paper` | `#f5f4f0` | Light slide background, practice cards | `src/styles/global.css:18` |
| `--white` | `#fff` | Text on dark slides, card surfaces | `src/styles/global.css:19` |
| `--accent` | `#e5222b` | Single accent stroke per icon, markers, focus ring | `src/styles/global.css:20` |
| `--line` | `#d9d8d3` | Hairlines on light | `src/styles/global.css:21` |
| `--reading-stone` | `#cfccc5` | Stone reading surface behind sheet pairs, icon masks | `src/styles/global.css:279` |
| stone (opening) | `#cfcdc7` | Opening slide background | `src/styles/global.css:135` |
| sheet light | `#dbd9d3`, `#e3e1db` | Opening paper slabs | `src/styles/global.css:170,180` |
| sheet pair | `#aaa79f` (back), `#e1ded7` (front) | Identity/what/purpose/closing sheets | `src/styles/global.css:342,350` |
| connector rule | `#b9b6af` | 1px vertical rule inside the verb list | `src/styles/global.css:437` |
| accent on dark | `#ff777b` | Eyebrow on `.approach` and `.robotics` | `src/styles/global.css:562,734` |
| hairline on dark | `#45474a` | Robotics capability separators | `src/styles/global.css:763` |
| secondary on dark | `#f0f0ee` | Robotics capability text | `src/styles/global.css:764` |
| dim on dark | `#c2c2c2` | Section index and secondary copy on dark | `src/styles/global.css:569,782,799` |
| plate surface | `#f5f1e9` | Light plate holding the robotics render | `src/styles/global.css:985` |
| plate border | `1px solid rgb(229 34 43 / 55%)` | Red hairline around the light plate | `src/styles/global.css:988` |
| card border | `1px solid #e3e1db` | Practice card outline | `src/styles/global.css:603` |

Contrast pairs approved by the stylesheet: `--ink` on `--paper`; `--white` on `--ink`;
`--accent` on `--paper`; `#ff777b` on `--ink` (the base `--accent` is **not** used for text on
dark); `#c2c2c2` on `--ink` for metadata.

## Typography

Font stack: `'Avenir Next', Avenir, Arial, Helvetica, sans-serif` (`src/styles/global.css:11`).
No webfonts are loaded; the deck renders with the stack's local fallback.

| Role | Size | Weight | Tracking / leading | Source |
| --- | --- | --- | --- | --- |
| Eyebrow | `0.72rem` | 700 | `0.16em` uppercase | `src/styles/global.css:226-236` |
| Section heading `h2` | `clamp(2.5rem, 7vw, 5.6rem)` | 600 | `-0.075em` / `1.03`, `max-width: 13ch` | `src/styles/global.css:400-406` |
| Display copy (`.approach-copy`, `.purpose-copy`) | `clamp(1.8rem, 5vw, 4.2rem)` | 500 | `-0.04em` / `1.25`, `max-width: 26ch` | `src/styles/global.css:563-568` |
| Lead / shared display copy | — | 500 | `-0.04em` | `src/styles/global.css:409-419` |
| List item | `clamp(1.25rem, 1.9vw, 1.6rem)` | 500 | `-0.025em` / `1.35` | `src/styles/global.css:444-450` |
| Section index | `0.65rem` | 600 | `0.12em`, muted | `src/styles/global.css:264-272` |

## Layout and spacing

| Rule | Value | Source |
| --- | --- | --- |
| Page gutter | `clamp(1.25rem, 6vw, 6.75rem)` | `src/styles/global.css:22` |
| Section padding | `clamp(5rem, 10vw, 9rem) var(--gutter)` | `src/styles/global.css:115-119` |
| Section height | `min-height: 78vh`, `100svh` from 760px | `src/styles/global.css:115,929-935` |
| Editorial frame | `width: min(100%, 70rem); margin: auto` | `src/styles/global.css:121-124` |
| Wide frame (opening, closing) | `82rem` | `src/styles/global.css:189,848` |
| Dark two-column grid | `0.8fr 1.2fr`, `gap: 5vw`, centred | `src/styles/global.css:976` |
| Sheet top offset | `clamp(1.25rem, 4svh, 3.5rem)` | `src/styles/global.css:277,646` |

Spacing is not a scale: it is continuous `clamp()` plus a few fixed gaps (`3rem` in the
stacked frame, `5vw` between columns, `0.25rem` between list items).

## Radius and elevation

| Rule | Value | Source |
| --- | --- | --- |
| Practice card | `border-radius: 1rem` | `src/styles/global.css:600-606` |
| Sheet pair radii | organic percentages, e.g. `0 0 72% 28% / 0 0 85% 35%` | `src/styles/global.css:342-361,374-379` |
| Opening slabs | `0 0 0 42%`, `48% 32% 0 0` | `src/styles/global.css:164-182` |
| Shadow | `0 12px 32px rgb(48 45 40 / 12%)` | `src/styles/global.css:164-182` |

Radii are a device, not a scale: large organic radii draw the paper sheets; `1rem` is the only
component radius.

## Component rules

- **Eyebrow + heading block** (`.section-heading`): eyebrow `NN — Label` above the `h2`, block
  capped by `h2 { max-width: 13ch }` (`src/styles/global.css:226-236,400-406`).
- **Icon**: inline SVG, `viewBox="0 0 24 24"`, `fill="none"`, `stroke="currentColor"`,
  `stroke-width="1.7"`, round caps and joins, `aria-hidden="true" focusable="false"`, exactly
  one child element carrying `.method-accent`/`.outcome-accent` in `var(--accent)`
  (`src/pages/index.astro:119-142,165-172`; `src/styles/global.css:465-467,547-549`).
- **Verb list** (identity): stacked rows with a 1px connector rule behind the icons; the icon
  masks the rule with `background: var(--reading-stone)` (`src/styles/global.css:431-467`).
- **Practice card**: white surface, `1px #e3e1db` border, `1rem` radius, 3rem PNG icon that
  shrinks to `2.25rem` at 1100px, accent list markers (`src/styles/global.css:600-642,1041`).
- **Light plate on a dark slide** (`.robotics-art`): `#f5f1e9` surface, red hairline border,
  `padding: clamp(1.5rem, 3vw, 3rem)`, `min-height: 30rem`, holding an image at
  `width: 100%; max-height: 27rem; object-fit: contain` (`src/styles/global.css:793-797,985-990`).
- **Section index**: absolutely positioned `NN / 08`, bottom right, `#50514f` on light and
  `#c2c2c2` on dark (`src/styles/global.css:264-272,196-199,569,799`).
- **Fixed logo**: white JPEG logo, `mix-blend-mode: multiply` on light and
  `background: var(--white)` when `[data-on-dark]` is set by JS against
  `.approach, .robotics` (`src/styles/global.css:44-66`; `src/pages/index.astro:284-300`).

## Motion

GSAP only, with a reduced-motion branch that skips it entirely (`src/pages/index.astro:281-315`):
word-split heading stagger at `top 88%`, `once` (`370-383`); `autoAlpha`/`y` reveals on the
`.approach-copy` (`384-396`); parallax `y: 16, scrub: 0.6` only on `.robotics-art img` and
`.closing-art img` (`433-447`); proximity scroll-snap excluding `.practices` from 760px.

Gap to respect when adding decoration: there is **no** CSS `prefers-reduced-motion` rule, so any
new CSS-only animation must add its own media query.

## Accessibility

- `a:focus-visible { outline: 3px solid var(--accent); outline-offset: 5px }`
  (`src/styles/global.css:108-113`).
- Decorative nodes carry `aria-hidden="true"`; icons add `focusable="false"`.
- The GSAP word split writes an `aria-label` on the heading and `aria-hidden` on the spans
  (`src/pages/index.astro:327-334`), so post-JS heading text lives in attributes.
- Any new dark or light surface placed under the fixed logo must be added to the on-dark
  selector list, or the logo keeps its white JPEG box.
