# skills

Portable, model-agnostic skills by [Jeremiah Dillon](https://jeremiahdillon.com). Each skill is a folder holding a `SKILL.md` in the [Agent Skills](https://agentskills.io) format, which Claude Code, Codex, Gemini CLI, and other agent harnesses can load directly. Skills are grouped by category:

```
<category>/<skill-name>/SKILL.md
```

## Index

| Category | Skill | What it does | Raw URL |
|---|---|---|---|
| writing | [long-form-essay-voice](writing/long-form-essay-voice/SKILL.md) | Drafts analytical long-form essays in Jeremiah's voice from rough ideas, an outline, or a draft. | [SKILL.md](https://raw.githubusercontent.com/jeremiahdillon/skills/main/writing/long-form-essay-voice/SKILL.md) |

## Toolkits

Some skills only make sense alongside the programs they drive, so they live with their code in a separate repository rather than here. They can't be fetched with the single-file recipe below; install them from their own repo.

| Toolkit | Skills | What it does | Requires |
|---|---|---|---|
| [claude-code-delegate](https://github.com/jeremiahdillon/claude-code-delegate) | `delegate`, `adversarial-review` | Lets Claude Code hand bounded work to cheap open-weight models (OpenRouter, OpenCode) and run automated adversarial review loops with a second model. | Claude Code, Python 3.9+, OpenCode, an OpenRouter API key |

## Fetching a skill

Every skill resolves to the same URL shape:

```
https://raw.githubusercontent.com/jeremiahdillon/skills/main/<category>/<skill-name>/SKILL.md
```

Install into Claude Code (personal skills live under `~/.claude/skills/<skill-name>/`):

```sh
SKILL=long-form-essay-voice
mkdir -p ~/.claude/skills/$SKILL
curl -sSL -o ~/.claude/skills/$SKILL/SKILL.md \
  https://raw.githubusercontent.com/jeremiahdillon/skills/main/writing/$SKILL/SKILL.md
```

For a harness that reads a skills directory from the project instead, clone the repo and point it at the category folder, or copy the one skill folder you want. For a plain chat model with no skill loader, paste the `SKILL.md` body as system or project instructions; the frontmatter is metadata and can be dropped.

## Conventions

The skill folder name and the frontmatter `name` are always identical, lowercase and hyphenated, and do not change once published, since they form the fetch URL. A skill is a single `SKILL.md` unless supporting material would bloat it, in which case the extra files sit beside it and `SKILL.md` says when to read them. Skill text is plain ASCII with straight quotes.

## License

Skills and this README are released under [CC BY 4.0](LICENSE). Short excerpts from the author's published essays quoted inside the skills remain copyright Jeremiah Dillon and are excluded from that grant; see the LICENSE header.
