# Art direction

Read this reference only in Phase 2 when the storyline is complete.

## Choose the direction

Start from audience, decision, content, brand assets, and emotion arc. Recommend one direction,
not a catalog. If the user's preference conflicts with readability or audience expectations,
keep their intent and adjust the execution.

Useful starting points—not fixed themes:

| Direction | Best for | Character |
|---|---|---|
| Editorial Signal | Leadership, strategy, thought leadership | Restrained palette, oversized type, asymmetric rules |
| Midnight System | Technology, innovation, data | Dark field, luminous accent, precise grids, subtle glow |
| Warm Modern | People, culture, customer stories | Warm neutrals, humane color, soft geometry, generous whitespace |
| Bold Swiss | Pitches and decisive recommendations | High contrast, strict grid, direct type, one vivid accent |

## Define the design contract

Record these decisions in `direction.html` and reuse them in `deck.html`:

- **Name and rationale** — one sentence connecting the style to audience and purpose.
- **Tokens** — background, surface, foreground, muted, accent, secondary accent, line, radius,
  shadow, spacing, and motion duration.
- **Typography** — system-font stacks and distinct display/body roles; no more than two roles.
- **Signature motif** — one repeated device such as a signal line, cropped circle, dot matrix,
  numbered rail, or paper edge.
- **Visual rhythm** — where the deck becomes quiet, dense, or high contrast.
- **Imagery** — treatment for supplied or available imagery; otherwise prefer purposeful CSS
  geometry and inline SVG over decorative stock imagery.
- **Charts** — line weight, label style, highlight behavior, and source treatment.
- **Motion** — one entrance language, normally 300–600ms, used only to clarify hierarchy.

Use the 70/20/10 color rule: roughly 70% ground, 20% supporting surface, 10% accent. Meet
accessible contrast before adding glow, gradients, translucency, or texture.

## Build the preview

Create `direction.html` as a self-contained file with exactly three slides using real content:

1. **Title** — tests first impression, hierarchy, and signature motif.
2. **Evidence or Big Number** — tests data emphasis, source treatment, and density.
3. **Comparison or Process** — tests structure, components, and responsive behavior.

Base it on `deck-template.html`, keeping navigation and accessibility behavior. Remove all
other example slides. The preview must work over `file://` with no network requests.

## Composition rules

- One dominant idea and one focal point per slide.
- Do not use cards unless the content is genuinely a set of peers.
- Vary composition while preserving tokens and motif.
- Use whitespace as structure; do not fill empty areas by default.
- Keep decorative elements behind content and visually subordinate.
- Direct-label charts when possible; do not make the audience decode a legend.
- Use a high-contrast pattern break around one-third and two-thirds of a longer deck.
- Keep source markers quiet but readable.

Avoid generic gradient blobs, glass effects on every surface, excessive rounded cards, tiny
body copy, unrelated icons, autoplay, continuous animation, and decorative charts.

## Approval

Present the direction name, rationale, palette, type roles, motif, rhythm, and motion in a
compact summary with the preview path. Revise only the requested visual variables. Do not
start the full deck until both storyline and direction are explicitly approved.
