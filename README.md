# Idea to Deck

An [Agent Skills](https://agentskills.io) skill for Codex and Claude Code that turns a raw concept into a researched, storylined, visually directed, self-contained HTML presentation through explicit approval gates.

The workflow approves research first, then the storyline and a three-slide visual direction
preview, before building and visually checking the complete deck.

## Codex

Ask Codex to install it:

```text
Use $skill-installer to install:
https://github.com/chanooooot/idea-to-deck-skill/tree/main/skills/idea-to-deck
```

Or run:

```bash
python3 ~/.codex/skills/.system/skill-installer/scripts/install-skill-from-github.py \
  --repo chanooooot/idea-to-deck-skill \
  --path skills/idea-to-deck
```

Invoke it with `$idea-to-deck`. If it does not appear immediately, restart Codex.

For a project-only installation, copy `skills/idea-to-deck` to `.agents/skills/idea-to-deck`
inside that project.

## Claude Code

Install it as a personal skill:

```bash
git clone --depth 1 https://github.com/chanooooot/idea-to-deck-skill.git /tmp/idea-to-deck-skill
mkdir -p ~/.claude/skills
cp -R /tmp/idea-to-deck-skill/skills/idea-to-deck ~/.claude/skills/
```

Invoke it with `/idea-to-deck`. For a project-only installation, copy the same folder to
`.claude/skills/idea-to-deck` inside that project.

The shared skill uses only the standard `name` and `description` frontmatter fields and does
not require platform-specific tools or companion skills.
