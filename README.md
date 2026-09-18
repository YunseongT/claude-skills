# claude-skills

A personal collection of skills for [Claude Code](https://docs.claude.com/en/docs/claude-code). Each skill is a self-contained directory with a single `SKILL.md`.

> 🇰🇷 한국어 README: [README.ko.md](./README.ko.md)

## Skills

| Skill | Description | Language |
|---|---|---|
| [`grill-me-p`](./grill-me-p) | Pedagogical Grill — relentlessly stress-tests edtech / educational web service plans from a critical educational-philosophy persona. | Korean |
| [`desoemat`](./desoemat) | Removes the machine texture of AI-generated Korean fiction by overwriting signals in a target voice instead of deleting them. | Korean |

> Some skills (like `grill-me-p`) are written in Korean because their persona, terminology interception, and tonal cues depend on Korean-language pedagogy discourse. Translating the `SKILL.md` would degrade behavior. The repository-level docs are in English; per-skill READMEs are bilingual.

## Installation

Drop each skill directory under `~/.claude/skills/` and Claude Code will pick it up automatically.

```bash
git clone https://github.com/YunseongT/claude-skills.git
cp -r claude-skills/grill-me-p ~/.claude/skills/
```

Or symlink it so repo updates apply instantly:

```bash
ln -s "$(pwd)/claude-skills/grill-me-p" ~/.claude/skills/grill-me-p
```

Restart Claude Code, then invoke a skill either by slash command (`/grill-me-p`) or by uttering one of the trigger phrases declared in its frontmatter.

## How invocation works

Each skill's `SKILL.md` frontmatter contains a `description` field that tells Claude **when** to load it. You don't need to memorize slash commands — natural language in the trigger language usually routes correctly.

Example:

- `/grill-me-p` or "이 에듀테크 기획 교육적으로 grill 해줘" → loads `grill-me-p`

## Contributing / Forking

Forks for personal use are encouraged. PRs welcome. When adding a skill:

1. Directory name in `kebab-case`.
2. `SKILL.md` must include frontmatter with `name` and `description`. The `description` should contain concrete trigger phrases so routing works.
3. Add a row to the **Skills** table above.
4. Provide a per-skill README. Bilingual is fine.

## License

[MIT](./LICENSE). Free to use, modify, and redistribute. When reusing skills whose prompts cite academic sources (e.g. Freire, Dewey in `grill-me-p`), please preserve the citations.
