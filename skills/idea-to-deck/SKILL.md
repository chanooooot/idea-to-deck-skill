---
name: idea-to-deck
description: Turn a raw concept into a researched, storylined, self-contained HTML presentation through explicit approval gates. Use for "idea to deck", "research this and build a presentation", or similar requests starting from an idea. Not for redesigning an existing deck.
---

# Idea to Deck

Turn a raw concept into a researched, storylined HTML deck. Run three phases in order, plus
an optional fourth. **Stop after every phase and wait for explicit approval. Never run two
phases in one reply.**

## Run state

Write each run to `decks/<slug>/`, where `<slug>` is a short kebab-case concept name:

| File | Purpose |
|---|---|
| `state.md` | Brief and explicit approval state |
| `research.md` | Phase 1 findings and source registry |
| `storyline.md` | Phase 2 approved argument and slide plan |
| `deck.html` | Phase 3 deck, edited in place by Phase 4 |

Create `state.md` before research:

```markdown
# Deck state
- Concept: ...
- Slug: ...
- Mode: quick | deep
- Language: th | en
- Audience: ...
- Intended decision or action: ...
- Approved through: intake | research | storyline | deck
- Last updated: YYYY-MM-DD
```

File presence is not approval. Advance `Approved through` only after the user explicitly
approves that phase. On resume, read `state.md` and continue after the last approved phase.
If artifacts exist without `state.md`, show what exists and ask which phase was approved;
never infer approval. Ask before replacing an unrelated existing run, but normal revisions
requested by the user may edit that phase's file.

## Intake

Default to **Quick**. Ask once, in one compact question, only for missing essentials: concept,
output language, audience, and what the audience should decide or do. If the user's language
preference is clear, use it instead of asking.

Use **Deep** only when the user requests it. Interview the user to surface the same essentials
plus constraints, risks, prior attempts, and what would change their decision. Do not ask the
Quick questions again after the interview. Persist the result in `state.md` and set
`Approved through: intake`.

Write research synthesis in the chosen output language. Preserve quotations in their original
language and add a short translation or paraphrase when needed.

## Phase 1 — Research

Goal: establish claims that are true and traceable.

Research directly with the available web-browsing tools and any sources the user supplied.
Do not delegate this phase: the result must remain synchronous with its approval gate.

- Prefer primary sources: official documentation, specifications, original papers, filings,
  announcements, and raw datasets.
- Follow secondary reporting to the original source before relying on its claim.
- For changing facts, prefer current sources and record publication dates.
- Seek two independent sources for a decisive quantitative claim. If only one credible source
  exists, keep the claim but flag the limitation instead of fabricating corroboration.
- Deliberately research the strongest counterpoint.

Assign every source a stable ID (`[S1]`, `[S2]`, ...). Use those IDs everywhere in the run.
Structure `research.md` as:

- **Core claims** — each claim followed by source IDs.
- **Evidence** — numbers, short quotations, and examples worth showing.
- **Counterpoints** — the strongest objection and the evidence behind it.
- **Open questions** — anything not verified.
- **Source registry** — ID, title, publisher or author, publication date, access date, and URL.

Every non-obvious claim needs at least one source ID. Never disguise inference as a sourced
fact.

Then stop. Summarize the core claims, strongest counterpoint, and open questions. Ask whether
to approve the research and proceed. Do not draft the storyline. When approval arrives, set
`Approved through: research` before Phase 2.

## Phase 2 — Storyline

Goal: decide the argument before designing slides.

Choose and name the narrative shape that fits the audience and purpose. Examples include
Situation → Complication → Resolution for persuasion, What → How → Use for an explainer,
Option A → Option B → Verdict for a comparison, or a chronological sequence for a process.

State the answer early rather than saving it for a reveal. Use one idea per slide and only
slides that change what this audience understands or decides. Ten to fifteen slides is a
ceiling for a deep deck, not a quota.

Use the slide type that fits each job: Title, Message, Context, Evidence, Comparison, Process,
Counterpoint, Takeaway, or Sources. Write `storyline.md` as a Markdown table:

```markdown
| # | Type | Headline | Support | Sources |
|---|---|---|---|---|
| 1 | Title | ... | ... | — |
| 2 | Evidence | A full-sentence claim | ... | [S1], [S3] |
```

Headlines must assert something; reading them in order should reveal the whole argument. Use
only source IDs from `research.md`.

Then stop. Show the storyline and ask for approval. Mention that the user may request a
stress-test interview. Do not build the deck. When approval arrives, set
`Approved through: storyline` before Phase 3.

## Phase 3 — Deck

Goal: render the approved storyline as `deck.html`.

Before building, read [references/html-build.md](references/html-build.md). Use
`references/deck-template.html` by default. Use reveal.js only when the deck actually needs
fragments, speaker view, nested slides, or another reveal-specific feature.

- Add no new claims. If a needed fact is absent from Phase 1, stop and research it through the
  Phase 1 gate.
- Keep each slide to a headline and at most three supporting points.
- Put source IDs beside every number and sourced claim; reproduce the registry entries on the
  closing Sources slide.
- Produce one complete, self-contained HTML file that opens over `file://` with no network
  requests, CDN assets, or webfonts.
- Preserve accessibility basics: correct document language, semantic headings, keyboard
  navigation, visible focus, sufficient contrast, reduced-motion behavior, and text
  alternatives for meaningful images and charts.

Verify the rendered deck as specified in `references/html-build.md`, then report its path and
ask for acceptance. Set `Approved through: deck` only after the user accepts it or explicitly
requests Phase 4.

## Phase 4 — Beautify (optional)

Run only when the user asks after `deck.html` exists. Use any available presentation-design
guidance, then edit `deck.html` in place; the skill must still work when none is installed.

Improve spacing, hierarchy, type scale, color, and visual distinction between slide types.
Do not add claims, slides, or reorder the argument. Keep the Phase 3 offline and accessibility
constraints. Re-run the same verification, then report the changes in one or two lines.

## Thai copy

- Keep familiar technical terms, product names, and code in their original language.
- Keep headlines short; do not invent spaces to force Thai line breaks.
- Use a loose enough line height for stacked vowels and tone marks, and inspect a dense slide.
