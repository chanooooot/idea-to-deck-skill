# HTML deck build and verification

Read this reference only for Phase 3 or Phase 4.

## Default build

Copy `deck-template.html` to the run's `deck.html`, replace its examples with the approved
storyline, set the document language and title, and delete unused example slides. Preserve
stable slide IDs (`slide-1`, `slide-2`, ...) so a specific slide can be opened as
`deck.html#slide-5` during verification.

Use system fonts. Inline all CSS, JavaScript, images, and chart code. Ordinary source links may
remain clickable, but loading the deck itself must issue no network requests.

For meaningful images, write useful `alt` text. For a chart, include a nearby text summary of
the conclusion and the underlying values; a canvas or SVG alone is not an accessible source.

## Optional reveal.js

Use reveal.js only for a feature the native template lacks, such as fragments, speaker view,
or nested slides. Install it in a scratch directory, then inline the UMD build and
`dist/reveal.css`; never reference a CDN.

- Skip bundled themes that import webfonts. Write a small system-font theme.
- Map theme variables explicitly on `.reveal` and heading rules; `reveal.css` does not do it.
- Put layout on an inner `.slide-body`, because reveal applies `!important` positioning rules
  to slide sections.
- Let reveal scale its virtual canvas; use fixed `rem` sizes rather than viewport units.
- Give each slide a stable hash route and retain the accessibility requirements from Phase 3.

## Charts

Prefer a large number or a small HTML table when it communicates the claim. Use any available
data-visualization guidance to choose the form, but do not require an extra skill. Add Chart.js
only when native HTML/CSS is insufficient, and inline its UMD build without its source-map
comment.

- Pass resolved colors to canvas code; canvas cannot resolve CSS variables.
- Rebuild charts when the color scheme changes.
- Ensure bar lengths encode the stated values from a common baseline.
- Show a sourced range as a stacked floor plus remainder, not as a floating bar.
- Do not invent a midpoint or other unsourced statistic for visual convenience.
- Include the source IDs, values, and a text summary next to the chart.

## Verification

The deck is not done until it has been rendered and inspected.

1. Check the file for leftover placeholders and external asset loads (`src`, CSS `url()`,
   imports, or scripts that fetch). Clickable source links are allowed.
2. Screenshot at a wide size such as 1400×900 and a compact size such as 800×600. Use an
   available browser tool, or locate Chromium/Chrome and allow a `CHROME_BIN` override rather
   than assuming one installation path.
3. Inspect light and dark modes. Respect `prefers-reduced-motion` rather than forcing motion.
4. Open at least one dense slide and every chart directly via its hash, for example
   `file:///absolute/path/deck.html#slide-5`; do not inspect only the title slide.
5. View each screenshot with the available image-viewing tool. Fix clipping, overflow,
   unreadable type, weak contrast, missing glyphs, misleading chart geometry, and broken focus
   states, then re-shoot.
6. Confirm keyboard navigation works and meaningful images/charts have text alternatives.

When using reveal.js, use its hash route (for example `#/4`) instead of modifying the HTML to
inject a jump script.
