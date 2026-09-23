# Design System Reference — v2.0

*Source of truth for the figma-designer agent. Regenerated 2026-08-03 by auditing the actual contents of [PriceLabs Design System v2](https://www.figma.com/design/vb7lmKk876GI7POdfOp6dL/PriceLabs-Design-System-v2) — replacing v1.0, which was drafted against the old "Design system 2024" library and contained aspirational token values that do not match production.*

*Key principle of this version: **the Figma v2 file mirrors the production Chakra theme** (`/agents/design-tokens/foundations/*` in code). Tokens below are the real values used in the product. Do not invent values; do not use the v1.0 values.*

---

## How this document relates to code and Figma

- Figma v2 file, page `02 — Foundations` = visual mirror of the Chakra theme in code.
- `tokens.css` / `tokens.json` (in this folder) = the same values for Claude Code prototyping.
- This doc = the contract the figma-designer agent reads before every task.

If a value here disagrees with the Figma v2 file or the Chakra theme, the Chakra theme wins — fix this doc.

---

## Conventions (as actually used in v2)

### Component naming
Component sets are named with a bare noun (`Button`, `Input`, `Tag`). Variants use property syntax:

- `Style=Primary, Size=sm, State=default`
- `Intent=neutral, Size=md, Removable=false`

Property order: **Style → Size → State → Intent/modifiers**.
Property **values are lowercase** (`default`, `hover`, `active`, `disabled`, `focus`, `filled`) and sizes are **t-shirt** (`xs / sm / md / lg`). This differs from the old 2024 library (numeric sizes `40/32/28`, capitalized states `Default/Hovered`) — the v2 convention is canonical for all new work.

### Page structure of the v2 file
| Page | Contents |
| :---- | :---- |
| 01 — Cover | (currently empty — needs a cover) |
| 02 — Foundations | Color, type, spacing, radius, shadow reference |
| 03 — Buttons | Button (96 variants), IconButton (36 variants) |
| 04 — Form & Inputs | Input, Checkbox, Radio, Switch |
| 05 — Display | Tag, Chip, Badge |
| 06 — Feedback | Alert, Toast, Tooltip, Skeleton, Spinner |
| 07 — Navigation | Tabs, Menu, Stepper |
| 08 — Overlays | Modal, Drawer, Popover |
| 09 — Data | Select, MultiSelect, SingleSelect, Table, Card, Divider, RangeSlider, SelectionCard |
| 10 — Example Screens | Composed screens |
| 11 — Mobile | BottomSheet, ResponsiveModal / ResponsiveDrawer / ResponsivePopover |
| 12 — Specialized | AlertDialog, DateRangePicker, ChipsTextInput, ChipsTextArea, PhoneNumber, Highlight |

The file also contains feature-work pages (Dark Mode explorations, Min/Max, Base Price Cleaning, Control Panel, Action Center, Vrbo Mapping, etc.) and an `Internal Only Canvas` holding legacy 2024-library components with the OLD naming convention. The agent must not source components from those pages.

---

## Tokens

All values live in `tokens.json` / `tokens.css` alongside this doc — the tables below are the human-readable summary.

### Color

**Brand — primaryRed scale.** Brand color is `primaryRed/600 #F37579`. Scale: 50 `#FEF1F2`, 100 `#FCDCDD`, 200 `#F69396`, 600 `#F37579`, 700 `#D66B6F`, 800 `#C36568`, 900 `#A15457`. (300–500 undefined.)

**Text & surface.** `primaryBlack #333333` (body), `secondaryBlack #7A7A7A` (supporting), `black #000000`, `buttonGrey #666666`, `disabledGrey #AEAEAE`, `disabledIcon #BDBDBD`, `productWhite #FFFFFF`, `backgroundGrey #F4F5F7` (page bg), `neutralGray #EFEFEF`, `softGray #E6E6E6`.

**Borders & dividers.** `borderColor #E0E0E0` (default), `tableBorderColor #EDF2F7`, `dividerGray #CBC5C5`, `headerSorting #B2B2B2`, `greenBorder #D6F3E8`, `redBorder #FCDCDD`, `blueBorder #98B7C7`.

**Status.** `blue #1976F3`, `secondaryBlue #1D69CD`, `surfaceBlue #E8F1FD`, `infoIcon #76A9FB`, `error #E63E3D`, `strongRed #D62828`, `amber #E29F08`, `warningAmber #FFC33A`, `yellow #FFD159`, `green #31C48D`, `lightGreen #4ADCA6`, `darkGreen #39AA80`.

**Highlight backgrounds.** `highlightBlue #F3F8FE`, `highlightRed #FEF1F2`, `highlightYellow #FEFAF3`, `highlightGreen #F5FBF9`.

**Chart palette.** `vividSkyBlue #2CAFFE`, `vividOrange #FE6A35`, `emeraldGreen #00E272`, `orchidPurple #D568FB`, `indigoBlue #544FC5`.

**Listing Optimizer grades.** excellent `#F5FBF9`/`#31C48D`, good `#F3F8FE`/`#1976F3`, needsReview `#FEFAF3`/`#E29F08`, low `#FEF1F2`/`#E63E3D`.

### Typography

IBM Plex Sans everywhere. Chakra size scale, desktop: `3xl 48/semibold`, `2xl 32/semibold`, `xl 24 (semibold, regular)`, `lg 18 (semibold, regular)`, `md 14 (bold, semibold, regular)` — **`md/semibold` is the default body style** — `sm 12 (semibold, regular)`, `xs 11 (semibold, regular)`. Mobile scale: `xl 24`, `lg 20`, `md 16`, `sm 14`, `xs 12`.

### Spacing

Chakra numeric scale, 1 unit = 4px: `px, 0.5, 1, 1.5, 2, 2.5, 3, 3.5, 4, 5, 6, 7, 8, 9, 10, 11, 12, 14, 16, 20, 24, 32, 40, 48, 56, 64, 80, 96` (= 1px through 384px). In Figma variables, periods become hyphens (`space-0-5`).

### Radius

16 named radii: `none 0`, `sm 2`, `base 4` (**button default**), `md 5`, `lg 10`, `xl 12`, `cardRadius 8`, `badge 15`, `dateRangePicker 3`, `dsoBand 25`, `mobileButton 25`, `mobileOutline 36`, `modalMobileTop 20`, `progressBar 18.6`, `circle 40`, `full`.

### Shadows

21 effect styles. Generic: `sm, base, md, lg, xl, 2xl` (Chakra values). Semantic — **prefer these over generic**: `shadow/button`, `shadow/card`, `shadow/modal`, `shadow/popover`, `shadow/menuList`, `shadow/pageHeader`, `shadow/inputActive`, `shadow/singleSelect`, `shadow/tags`, `shadow/floatingBanner`. `[ACTION]` Exact values of the semantic styles need to be recorded here from the Figma effect styles.

**`shadow/pageHeader` (measured off production 2026-09-03):** `0 2px 4px rgba(0,0,0,.05)`.

### Page header band (non-negotiable pattern)

Every full-page header band (e.g. Dynamic Pricing → Customizations, and the
single-listing Review Prices header) is a **full-width WHITE band on the
#F4F5F7 page** — never transparent — with a drop shadow so it reads as a
layer above the content:

- Standard page header: white bg, `padding: 10px 16px`,
  shadow `0 2px 4px rgba(0,0,0,.05)` (= `shadow/pageHeader`).
  Kicker (product-area label) 12/600 `#7A7A7A` uppercase, 4px below-gap;
  title 18/600 `#333333`.
- Listing header on Review Prices (heavier variant, measured): white bg,
  `padding: 6px 12px`, shadow `0 4px 6px -1px rgba(0,0,0,.1), 0 2px 4px -1px rgba(0,0,0,.06)`.
- Leave a band→content gap of **page background**, not white: 30px on
  Customizations (band → tab row), 12px on Review Prices (band → card).

*Recorded 2026-09-03 after the white bg + shadow were dropped twice in a row
in replicas (Review Prices, then Customizations). If a header band looks
flat or flush against the content, this is what's missing.*

---

## Component inventory (what exists in v2)

### Primitives
- **Button** `[IN LIBRARY]` — 96 variants. `Style` (Primary, Secondary, Ghost, Hyperlink, Blue…) × `Size` (sm/md/lg) × `State` (default/hover/active/disabled).
- **IconButton** `[IN LIBRARY]` — 36 variants.
- **Input** `[IN LIBRARY]` — Size (xs/sm/md) × State (default/hover/focus/filled/error/disabled).
- **Checkbox / Radio / Switch** `[IN LIBRARY]`. Checkbox values are recorded
  below under *Checkbox*; Radio and Switch are still unrecorded.
- **Select / SingleSelect / MultiSelect** `[IN LIBRARY]` (09 — Data).
- **RangeSlider** `[IN LIBRARY]`. Single-value Slider `[GAP]`.
- **DateRangePicker** `[IN LIBRARY]` (12 — Specialized). Single DatePicker `[GAP]`.
- **ChipsTextInput / ChipsTextArea / PhoneNumber** `[IN LIBRARY]` (12 — Specialized).
- **Plain Textarea** `[GAP]`.

### Display
- **Tag** `[IN LIBRARY]` — Intent × Size (md/lg) × Removable.
- **Chip, Badge** `[IN LIBRARY]`.
- **Highlight** `[IN LIBRARY]` (12 — Specialized).
- **Avatar / AvatarGroup** `[GAP]`.

### Feedback
- **Alert** `[IN LIBRARY]` — Intent (error/warning/info/success).
- **Toast** `[IN LIBRARY]` — Intent (error/warning/info/success).
- **Tooltip, Skeleton, Spinner** `[IN LIBRARY]`.
- **Empty State pattern component** `[GAP]`.
- **Progress Bar / Progress Ring** `[GAP]` (a `progressBar` radius token exists, component doesn't).

### Navigation
- **Tabs, Menu, Stepper** `[IN LIBRARY]`.
- **Side Navigation, Top Navigation, Breadcrumb, Pagination, Page Header** `[GAP]`.

### Overlays
- **Modal** `[IN LIBRARY]` — Size (xs/sm/md/lg/full).
  **Minimum height: 400px.** Applies at every size. Header and footer keep their
  intrinsic heights and the body absorbs the slack, so the footer stays pinned to the
  bottom edge rather than floating up under short content. In CSS: `min-height: 400px`
  on the modal with `display:flex; flex-direction:column`, `flex-shrink:0` on header and
  footer, `flex:1 1 auto` on the body.
  *Set by Abhijith 2026-08-19. Not yet reflected in the Figma v2 Modal component — record
  it there and drop this note once it is.*
- **Drawer, Popover** `[IN LIBRARY]`.
  **Popover minimum height: 300px**, same body-absorbs-the-slack rule as Modal. Unlike a
  modal it has no overlay — it anchors to whatever was clicked and leaves the page live.
  Border `#E0E0E0`, radius 8, body and footer `16px 24px` separated by paired shadows
  (`0 2px 2px` / `0 -2px 2px` of `rgba(51,51,51,.1)`), plus a slight outer lift on the
  sides and bottom: `0 4px 10px -2px rgba(51,51,51,.12)` — the y-offset keeps the top
  edge clean. Reference: Figma Miscellaneous 189-7047.
  *Set by Abhijith 2026-08-19; the outer shadow is not in the Figma frame — added so the
  floating layer reads as raised. Record both in the Figma component.*
- **AlertDialog** `[IN LIBRARY]` (12 — Specialized).

### Data
- **Table** `[PARTIAL]` — 2 component sets exist; row/header/cell coverage and empty/loading/error table states need audit.
- **Card, Divider, SelectionCard** `[IN LIBRARY]`.
- **Stat / Metric Card** `[GAP]`. Chart color sequence beyond the 5 categorical colors `[GAP]`.

### Mobile
- **BottomSheet, ResponsiveModal, ResponsiveDrawer, ResponsivePopover** `[IN LIBRARY]`.

---

## Component corrections & additions from prototyping (2026-09-03)

*Recorded per Abhijith's standing instruction: whenever he explicitly corrects a
component's design during prototyping, it lands here — measured values marked
`[measured]` (getComputedStyle off production), his design rulings marked
`[ruling]`. If a later instruction conflicts with an entry below, STOP and
surface the conflict before changing anything.*

### Button / Secondary
- Base `[measured]`: white bg, 1px `#E0E0E0` border, radius 4, `shadow/button`
  (`0 1px 2px rgba(51,51,51,.1)`); 14/600 text; heights 32 (compact) or 40.
- **Sizing `[ruling 2026-09-05]`: every text button (primary and secondary,
  32 and 40) has `min-width: 80px` and `padding: 0 16px`**, content centred.
  Icon-only buttons stay 32×32 squares. (Production measures Today at
  `0 12px` pad — the ruling deliberately widens it; keep 16px.)
- **Hover `[ruling]`: bg `#FEF1F2` (coral wash) + text/border coral `#F37579`.**
  This is the canonical hover recipe other interactive items reference.

### Tabs (page-level, "enclosed")
- `[measured]` 48px tall, 14/600; active = coral text + **5px coral top
  border**, radius 5 on the outer top corner, no bottom border (merges into
  panel); inactive = 1px `#E0E0E0` bottom border + 1px `rgba(0,0,0,.1)` left
  border (no right borders); **the white strip ends with the last tab
  `[ruling 2026-09-05]`** — the remainder of the row is page bg `#F4F5F7`
  (still carrying the 1px bottom border).
- Padding `[measured + ruling: don't cramp]`: generous sides — implement as
  measured min-widths with centred content: **Calendar 176 / Neighborhood
  Data 173 / Hotel Data 120 / Booking Insights 164** (2026-09-05). Never let
  a tab collapse to its 16px-padded natural width.
- Inactive tabs carry a **1px `rgba(0,0,0,.1)` border on TOP and LEFT**
  `[ruling]` (plus the 1px `#E0E0E0` bottom border).
- **Hover `[ruling]`: coral shades — `#FEF1F2` wash bg + coral text, and the
  top/left borders turn coral too** (the secondary-button hover recipe).
  Applies to inactive tabs only.

### Sub-tab pills (second-order tabs)
- `[measured]` 34px tall, 8px 12px padding, radius 5; labels **14/600 in every
  state** — active changes color only (coral on `#FEF1F2`), never weight.
- Row: 8px 16px padding + 1px `rgba(0,0,0,.1)` bottom divider.
- **Hover `[ruling]`: text color change only (→ coral). NO background.**

### Switch (toggle)
- `[measured]` 40×22 track, radius 11, 18px knob with 2px inset.
- On = green `#31C48D` `[measured]`. **Off = `#A0AEC0` (darker grey) `[ruling]`**
  — not Chakra's light `#CBD5E0`. (Off value eyeballed from Abhijith's
  reference image; pin from live if an off-state toggle is ever measurable.)

### List item (sidebar / customization / profile lists)
- `[measured]` 14/400, `#1A202C`; active/selected = coral text on `#FEF1F2`.
- **Hover `[ruling]`: text color only (→ coral), NO background** — same as the
  sub-tab hover. Never a grey hover. *(Corrected 2026-09-03: an earlier entry
  here claimed coral-shades hover — that was a transcription error, not an
  Abhijith ruling; the coral-shades hover belongs to Tabs and Secondary
  buttons.)*

### Form patterns (config panels)
- Config panel `[measured]`: bg `#F4F5F7`, radius 5, 24px 12px 12px padding.
- Field label `[measured]`: 12/600 `#333`, 8px below-gap; required = red `*`.
- Hint text `[measured]`: 11/400 `#7A7A7A` (e.g. "Between -80% and 500%").
- Inputs `[measured]`: 40px, radius 4, 1px `#E0E0E0`; inline suffixes 12/600 —
  units (`Night(s)`, `Day(s)`, `%`) in `#7A7A7A`, "% Premium" in green
  `#31C48D`.
- **Joiner words** ("for gaps between", "and") `[ruling]`: normal **14/400**
  text — NOT label style — vertically centered to the input boxes; a wrapped
  leading joiner right-aligns in a first column sized to the row above so the
  following input left-aligns with the input above it.
- Inline summary after a status tag (e.g. after the grey "Custom" tag)
  `[ruling]`: **12/600**, same as field labels.

### Links
- **"Learn More" (and peer inline doc links) are always semibold (600)
  `[ruling]`**, blue `#1976F3`. ("How Does It Work?" already 14/600.)
- Known production inconsistency `[measured]`: the Customizations **Info box**
  link renders `#0D6EFD` — flagged, not adopted. Figma 444-541's fifth frame is
  a hyperlink example and should settle this; see *Info box* `[ACTION]`.

### Info box
**Component name is "Info box" `[ruling]`** (Abhijith, 2026-09-07). Previously
filed here as "Info banner (blue)" — that name is retired; the component is one
set with a colour variant, not a blue-only element. Figma:
[RM-AI-MVP 444-541](https://www.figma.com/design/CWfsvb3Vep7QJYgDj6aXdX/RM-AI-MVP?node-id=444-541).

Shared shape, from the blue variant as measured in production:
- `[measured]` 1px border, radius 5, 12px 16px pad, icon + text in a row, 10px gap.
- **Body text 14/400 `#333` `[ruling]`** (not 12px) — holds for every variant.
- Icon takes the variant's accent colour `[measured]` on blue, 12px.

Four colour variants. Each pairs a `--pl-highlight-*` background with the
matching `--pl-status-*` accent for border and icon. The same four pairings are
corroborated independently by the Listing Optimizer grade tokens
(`--pl-lq-*-bg` / `--pl-lq-*-text`), which is why the mapping is recorded here
rather than treated as a guess:

| Variant | Background | Border + icon | Tokens |
|---|---|---|---|
| Info    | `#F3F8FE` | `#1976F3` | `--pl-highlight-blue` / `--pl-status-blue` |
| Success | `#F5FBF9` | `#31C48D` | `--pl-highlight-green` / `--pl-status-green` |
| Warning | `#FEFAF3` | `#E29F08` | `--pl-highlight-yellow` / `--pl-status-amber` |
| Error   | `#FEF1F2` | `#E63E3D` | `--pl-highlight-red` / `--pl-status-error` |

Only the **Info** row is `[measured]`; the other three are `[proposed]` — the
token pairs are real production values, but that these are the four the Info box
actually uses is inferred from the token structure, not read off the frame.

`[ACTION]` Still to confirm against Figma 444-541 (blocked: no Figma MCP access
in this account as of 2026-09-07):
- **Per-variant icons.** Info uses `fa-circle-info` `[measured]`. The other
  three are unrecorded — do not assume `fa-circle-check` /
  `fa-triangle-exclamation` / `fa-circle-exclamation` without checking.
- Whether every variant really carries the 1px accent border, or some are
  fill-only.
- Variant naming in the Figma component set (Info/Success/Warning/Error vs
  Info/Positive/Caution/Negative etc.) — this doc should use the set's own names.
- The **fifth frame is a hyperlink example**, which likely settles the link
  colour conflict recorded under *Links* below: production's info box link
  renders `#0D6EFD` while the standing ruling makes inline doc links `#1976F3`.
  Read that frame and resolve it in one place — currently the inconsistency is
  flagged but unadopted, so implementations disagree.

### Checkbox
Figma: [RM-AI-MVP 445-706](https://www.figma.com/design/CWfsvb3Vep7QJYgDj6aXdX/RM-AI-MVP?node-id=445-706)
(a checkbox group with every state). Was listed above only as
`[IN LIBRARY]` with no recorded values; these are the first.

- `[measured]` 16x16 box, 1px `#7A7A7A` border, radius 2, white fill.
- `[measured]` Checked: fill and border both coral `#F37579`, with a white
  check glyph at 10px.
- Label sits 10px to the right of the box. `[measured]` 12/400 `#333` in the
  Custom Seasonal Profile's column menu — note this is 12px, not the 14/400
  body ruling that governs the Info box; the two menus in that toolbar
  therefore disagree (the Upload/Download menu items are 14/400).
- **Never a native `<input type="checkbox">` with `accent-color`** `[ruling]`:
  `accent-color` cannot render the white check on a coral fill, so the control
  is a `role="checkbox"` button whose `aria-checked` drives the visual state.

`[ACTION]` The states above are the two the product currently shows, taken
from the measured Length of Stay Pricing table checkbox. Still to read off
Figma 445-706 (blocked: the Figma **Dev Mode MCP Server** is not enabled in
the desktop app, so the node cannot be fetched even though the Figma tools are
connected):
- hover, focus, disabled, and indeterminate states,
- whether the checked fill is really coral `#F37579` or a deeper red — it reads
  more saturated in the reference screenshots than in the measured product,
- the group's spacing/label rules as a component set.

### Status tags
- `[measured]` "No Rule Applied" / "Custom": white 12/500 on `#7A7A7A`,
  radius 4, 3px 8px pad. "Auto-applied": same but green `#31C48D`.
  "Unsaved": amber `#E29F08` text + 1px amber border, 12/600, radius 4.

### Pricing-calendar specifics
- Price chip `[measured + ruling]`: radius-800 pill spanning the **full cell
  width** (2px insets); hover = `rgba(0,0,0,.14)` darkening; the chip is the
  ONLY hover/tooltip trigger — **cells themselves have no hover state**.
- Grid lines `[measured]`: 1px white borders + 0.5px `#E0E0E0` inset hairline
  (never solid grey — it muddies the demand fills).
- Demand fills (Figma Audit 23-43): low `#DDF8C5`, normal `#B9E4BC`,
  good `#C8E8FB`, high `#A3CBE1`, unavailable `#E0E0E0`.
- Prices render as plain integers `[ruling]` — no decimals, no "K".

## Remaining gaps (build queue)

**P0** — Side Navigation, Top Navigation, Page Header, Empty State
**P1** — Avatar, Textarea, single-value Slider, single DatePicker, Pagination, Breadcrumb, Table row/header/state audit
**P2** — Progress Bar / Ring, Stat Card, extended chart sequences, Cover page for the file

---

## Decision rules for the agent (carried over, still valid)

- Reuse over create. Source components only from pages 03–12, never from `Internal Only Canvas`.
- Refuse silent deviation — flag missing tokens, propose additions.
- Every screen ships empty / loading / error states unless told happy-path only.
- Never two filled Primary (coral) buttons on one screen; destructive next to affirmative demotes to Ghost + error color; filled red only as the sole primary action in a confirmation dialog.
- New patterns get documented and surfaced for promotion into this doc.

## Changelog
- **2026-09-05** — Button sizing ruling: text buttons get `min-width: 80px` +
  `0 16px` padding (icon buttons stay square). Tabs: recorded production
  min-widths (Calendar 176 is much wider than its label) and the ruling that
  the white tab strip ends at the last tab — the rest of the row is page bg.
- **2026-09-03 (later)** — Added **"Component corrections & additions from
  prototyping"**: secondary-button hover recipe, tab paddings, sub-tab pill
  weights + text-only hover, switch off-track `#A0AEC0`, list-item coral hover,
  form joiner/label/hint/suffix patterns, semibold Learn More links, 14px info
  banner text, status tags, and pricing-calendar chip/grid/demand rules.
  Standing process: explicit design rulings from Abhijith are recorded here as
  they happen; conflicts with prior rulings get surfaced before overriding.
- **2026-09-03** — Recorded the **page header band pattern** (white bg +
  `shadow/pageHeader: 0 2px 4px rgba(0,0,0,.05)`, kicker/title specs, and the
  band→content page-bg gap) under Shadows, after two replicas in a row missed
  it. Also measured: sub-tab pill labels are **14/600 in every state** (active
  changes color only), and the sub-tab row carries a 1px rgba(0,0,0,.1)
  bottom divider.
- **2026-08-19** — Modal gains a 400px minimum height (see Overlays). Recorded a split
  focus-state rule: text inputs focus coral `#F37579` + `0 0 4px rgba(243,117,121,.25)`
  (Figma Miscellaneous 144-3034); every other control keeps blue `#1976F3`. The
  `shadow/inputActive` value is still an unrecorded `[ACTION]` above — this is likely it.
- **2026-08-03 v2.0** — Regenerated from the actual PriceLabs Design System v2 Figma file. Replaced v1.0 aspirational tokens with production Chakra values. Updated component inventory: most v1.0 P0/P1 gaps are now built. New gap list reflects reality. Canonical naming convention switched to v2 style (lowercase states, t-shirt sizes).
- **2026-05-08 v1.0** — (superseded) Locked tokens drafted from the old 2024 library + proposals.
