# grill-me-p — Pedagogical Grill

A Claude Code skill that interrogates educational web service / edtech plans through the persona of a 20-year-veteran critical educational philosopher. No praise, no empathic cushioning, no filler — only the question **"Is this plan pedagogically and humanistically justified?"**, pressed through open-ended Socratic challenges.

> The skill operates **in Korean**. The persona, terminology interception, and tonal cues are tightly coupled to Korean-language pedagogy discourse, so the prompt is intentionally not translated. This README explains what the skill does to non-Korean readers. 🇰🇷 한국어판: [README.ko.md](./README.ko.md)

## What it does

It plays a **pacemaker**, not a wrecking ball: the goal is to help the planner's educational philosophy take root *coherently* on top of the actual UI/UX structure. When a user submits a plan for a learning app, LMS, AI tutor, or other student-facing product, the skill picks the single most damaging blind spot from five academic axes below and fires one open-ended question at it.

## The five critique axes

| # | Concept | Source |
|---|---|---|
| 1 | Banking concept of education / Praxis | Paulo Freire, *Pedagogy of the Oppressed* (1968/70) |
| 2 | Continuity of experience | John Dewey, *Experience and Education* (1938) |
| 3 | Maieutics / Elenchus | Socrates (Plato's early dialogues) |
| 4 | Illusion of mastery in AI-mediated learning | Tom Chatfield et al.; related: D. Willingham on metacognitive illusion |
| 5 | Collective agency vs. isolated human-AI interaction | Human-Centered AI in Education discourse (Stanford HAI, UNESCO's *AI and Education* guidance) |

### Citation disclaimer

Axes 1–3 sit on well-established canonical sources and can be cited directly. **Axes 4 and 5 reference a contemporary discourse cluster rather than a single canonical work** — the names listed are entry points, not the sole or definitive authorities. If you are writing for an academic venue, treat the citations here as starting pointers and verify a primary source that matches the specific claim you are making. The skill itself uses these names as *rhetorical anchors* for critique, not as bibliographic authority.

## Developmental-stage framing

Before pressing, the skill infers the learner population and adjusts which theoretical frame leads the critique.

| Audience | Primary frame |
|---|---|
| Early elementary | Piaget (preoperational / concrete operational), Vygotsky (ZPD) |
| Late elementary – middle school | Concrete → formal operational transition, Erikson (identity) |
| High school | Formal operational, Kohlberg (postconventional morality) |
| University / adult | Mezirow (transformative learning), Knowles (andragogy) |
| Teachers / institutions | Shulman (PCK), institutional accountability |

## Install

```bash
# Option A: copy
cp -r grill-me-p ~/.claude/skills/

# Option B: symlink (repo updates apply instantly)
ln -s "$(pwd)/grill-me-p" ~/.claude/skills/grill-me-p
```

Restart Claude Code to register the skill.

## Invocation

- Slash: `/grill-me-p`
- Auto-trigger (Korean phrasing, since the skill runs in Korean):
  - "이 에듀테크 기획 교육적으로 비판해줘"
  - "AI 튜터 UI 흐름 철학적으로 grill 해줘"
  - "학습용 앱 기획 검토해줘"

For non-educational product or code-design grilling, use `grill-me` instead — `grill-me-p` deliberately scopes itself to educational contexts.

## Operating flow

1. **Audience profiling** (internal; no output)
2. **Pick one of the five axes** — the most damaging blind spot in the plan
3. **One open-ended question** — single turn, single question, header tagging the axis, no multiple choice
4. **Concept interception + scaffolded follow-up** — quote a slippery word from the answer, expose the gap between its ideal value and the concrete UI/UX, then ask a question that pushes the planner to redesign the *means* rather than handing them an answer
5. **Terminate and summarize** when (a) the planner has aligned answers across at least 3 of the 5 axes, (b) the user asks to stop, or (c) the same axis has circled three times without progress

Full prompt: [`SKILL.md`](./SKILL.md).

## License

MIT — see [LICENSE](../LICENSE) at the repository root.
