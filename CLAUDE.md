# PriceLabs Prototype Kit

You are working on a PriceLabs prototype: one or more self-contained HTML base pages
downloaded from the PL Prototype Gallery, plus this design context. The pages are
production-accurate replicas — every value was measured off the live product with
`getComputedStyle`, not eyeballed. Build on top of them; don't degrade them.

## The files here

- `pricelabs-*.html` — base page(s). Each has a `PL-RESOURCE-PROVENANCE` comment in its
  header (resource id + version + download date). **Never remove or edit that comment** —
  it's how changes get merged back into the shared resource.
- `design-system-v2.md` — the design system reference. **Read it before styling anything.**
- `tokens.css` / `tokens.json` — production design tokens (Chakra theme mirror).

## Design rules (non-negotiable)

- Tokens come from `tokens.css` — never invent values.
- IBM Plex Sans everywhere. Default body: 14px/600. Text #333333, secondary #7A7A7A.
- Coral #F37579 = primary buttons, brand accents, text-input focus. Logo red #E63E3D is
  a different red — don't swap them.
- Focus states: **text inputs focus coral** (1px #F37579 + `0 0 4px rgba(243,117,121,.25)`);
  **everything else focuses blue #1976F3**. Never violet.
- Page bg #F4F5F7, borders #E0E0E0.
- **Info box** (the callout component — *not* "info banner", that name is retired) is one
  component with four colour variants. Each pairs a highlight background with the matching
  status accent for its border and icon: info `#F3F8FE`/`#1976F3`, success `#F5FBF9`/`#31C48D`,
  warning `#FEFAF3`/`#E29F08`, error `#FEF1F2`/`#E63E3D`. Shared shape: 1px accent border,
  radius 5, 12px 16px pad, body text **14/400** #333 (not 12px). Per-variant icons are not
  yet confirmed — only info (`fa-circle-info`) is measured, so check before picking one.
- Icons are Font Awesome Pro 6.7.2 via the kit script already in each page
  (`kit.fontawesome.com/46535d3fdd.js`) — never hand-roll SVG paths for generic UI icons.
  Size icons via `font-size` on the parent, never width/height on the SVG. Icons load
  async: a DOM query right after page load reports zero icons — screenshot to verify.
- `-webkit-font-smoothing: antialiased` is required on html/body (already set) — removing
  it makes every font weight render heavier on macOS. It is not a font-weight bug.

## Working constraints (keep the file mergeable)

- Keep each page **self-contained**: inline CSS/JS, no build step, no external deps
  beyond Google Fonts + the FA kit already in the file.
- Stay **path-portable**: no root-relative `src`/`href` (`/...`). The same file must work
  served from any folder and opened via `file://`.
- **No localStorage** — prototypes are ephemeral-state demos. Bake decisions into seed data.
- Prefer adding to existing patterns over restructuring: big rewrites make your changes
  impossible to merge back cleanly.

## Sending work back

Built something reusable — an interaction, a missing state, a richer behavior? Send the
edited `.html` file itself back to Abhijith (Slack), with the provenance comment intact.
Do NOT use the browser's File → Save As (it saves the rendered DOM, not the source, and
that can't be merged) — send the file you were editing.
