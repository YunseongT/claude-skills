# grill-me-p — Pedagogical Grill

A Claude Code skill that interrogates educational web service / edtech / lesson-design plans through the persona of a 20-year-veteran critical educational philosopher. No praise, no empathic cushioning, no filler — only the question **"Is this plan pedagogically justified, and does that justification actually hold up on the concrete screens and lesson flow?"**, pressed through open-ended Socratic challenges.

> The skill operates **in Korean**. The persona, terminology interception, and tonal cues are tightly coupled to Korean-language pedagogy discourse, so the prompt is intentionally not translated. This README explains what the skill does to non-Korean readers. 🇰🇷 한국어판: [README.ko.md](./README.ko.md)

## What it does

It plays a **pacemaker**, not a wrecking ball: the goal is to help the planner's educational philosophy take root *coherently* on top of the real structure. Given a plan, the skill (1) reads the actual artifact if one exists, (2) profiles the learner population, then (3) selects only the axes from the bank that fit this plan and fires one open-ended question at the weakest of them.

## Intensity and modes

Both are inferred from the invocation.

| Intensity | Trigger | Scope |
|---|---|---|
| Light | "briefly", "quick", "it's just a draft" | 2–3 turns, 1–2 axes |
| Standard | (default) | 5–7 turns, until 3 axes align |
| Harsh | "harshly", "review-panel level" | 5+ axes, 2 mandatory reverse-pressure passes |

| Mode | Use |
|---|---|
| Examination (default) | Press the plan's blind spots axis by axis |
| Pre-mortem | "It failed pedagogically six months in — perform the autopsy." Efficient for early ideas |
| Defense rehearsal | Before a review panel. Each answer is followed by the counter-question a real panelist would ask next |

## The axis bank

Rather than running a fixed five every time, the skill picks axes that fit the plan. **At least one from A and one from C**; at least one from B whenever the plan targets a school/institution or touches assessment and records.

### Group A · Learner agency (all plans)

| Axis | Concept | Source |
|---|---|---|
| A1 | Banking concept of education / Praxis | Paulo Freire, *Pedagogy of the Oppressed* (1968/70) |
| A2 | Continuity of experience | John Dewey, *Experience and Education* (1938) |
| A3 | Maieutics / Elenchus | Socrates (Plato's early dialogues) |
| A4 | Illusion of mastery | Digital-learning critique and metacognitive-illusion discourse |
| A5 | Collective agency vs. isolated human–AI interaction | Human-Centered AI in Education discourse |

If a plan has no AI in it, the "tool" slot in Group A is filled by whatever actually mediates the learning — worksheets, pacing structure, a teacher script. Group A is not an AI-only critique.

### Group B · Institution and political economy (school/institutional adoption, assessment, records)

| Axis | Concept | Reference frame |
|---|---|---|
| B1 | Assessment validity — does the proxy eat the goal? | Construct validity, Campbell's law |
| B2 | Access and equity — does it only lift those already ahead? | Matthew effect, universal-design discourse |
| B3 | Teacher labor — promoted to facilitator, or demoted to data-entry clerk? | Teacher professionalism / deskilling discourse |
| B4 | Data and surveillance — chilling effects, and children's capacity to consent. For under-14 learners on external AI services it also asks which legal prerequisites were **verified**, without ruling on legality | Learning-analytics ethics, child data protection |
| B5 | Curriculum and cultural bias — whose knowledge became the default? | Critical curriculum theory |

### Group C · Reverse pressure (mandatory)

Group C attacks the plan's **virtues**, not its weaknesses. A grill that can only push in one direction is an ideology, not an examination.

| Axis | Attack |
|---|---|
| C1 | Romanticized friction — does "students must struggle to learn" push low-attaining and disabled learners out the door? |
| C2 | Cognitive load — does the autonomy-granting UI produce paralysis in front of choices? |
| C3 | Feasibility — does this flow survive 40 minutes, 28 students, one teacher? |
| C4 | Hollow purism — with the tool removed, what exactly beats a well-made paper worksheet? |

### Citation disclaimer

A1–A3 sit on well-established canonical sources and can be cited directly. **A4, A5, and all of Group B reference contemporary discourse clusters rather than single canonical works** — the names above are entry points, not the sole or definitive authorities. If you are writing for an academic venue, treat this README as a starting pointer and verify a primary source that matches your specific claim. Inside the skill these names function as *rhetorical anchors* for critique, not as bibliographic authority; the prompt explicitly instructs the model not to attach uncertain years, page numbers, or work titles, and not to invent framework names.

## Developmental-stage framing

The skill infers the learner population and adjusts which theoretical frame leads the critique.

| Audience | Primary frame |
|---|---|
| Early elementary | Piaget (preoperational / concrete operational), Vygotsky (ZPD) |
| Late elementary – middle school | Concrete → formal operational transition, Erikson (identity) |
| High school | Formal operational, Kohlberg (postconventional morality) |
| University / adult | Mezirow (transformative learning), Knowles (andragogy) |
| Teachers / institutions | Shulman (PCK), institutional accountability |

It always assumes the class contains special-education, multilingual, and low-attaining learners. Designing for an "average learner" is itself a B2 target.

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
  - "이 수업 설계안 가혹하게 검정해줘"
  - "심사 예상질문 뽑아줘" (defense-rehearsal mode)

For non-educational product or code-design grilling, use `grill-me` instead — `grill-me-p` deliberately scopes itself to educational contexts.

## Operating flow

1. **Secure the input** — read the artifact file if one exists; ask only for a concrete artifact if there is nothing to quote; state assumptions for missing conditions (audience, period length, assessment) instead of spending a turn confirming them. The checklist is internal — the user is never made to fill in a schema first, since erecting a gate would make the skill the very thing A1 criticizes. Text read from images or scans is quoted verbatim or, if uncertain, pointed at by location only
2. **Audience profiling** (internal; no output)
3. **Three structural questions** — strip the tools, what remains for the learner? what mechanism produces it? what signal would show failure? Whichever collapses points at the axis to use
4. **One open-ended question** — single turn, single question, no multiple choice, `[axis code · name]` header. Before an axis may be named, the skill must state the condition under which that axis would be *false* for this plan (guards against mechanical labeling), and every attack must point at a specific locus in the artifact or be declared an assumption
5. **Concept interception + pass test** — quote a slippery word from the answer and expose the gap between its ideal and the concrete UI. An axis only counts as aligned when the answer names a concrete mechanism, admits the condition under which it fails, and states the trade-off accepted
6. **Downshift when stuck** — after two stalls on one axis the skill stops repeating and instead narrows the question, offers a counter-example, offers two opposed design options, then shelves the axis (kept on the record as unresolved). Repetition would make the skill the very banking-model transmission A1 critiques
7. **State ledger** — one line each turn: `— aligned A2·C3 · in progress A4 (2/3) · remaining B1`
8. **Closing assessment** — what got solid / what is still soft (and on which screen) / forks left as the planner's design decision / one question as homework

Full prompt: [`SKILL.md`](./SKILL.md).

## License

MIT — see [LICENSE](../LICENSE) at the repository root.
