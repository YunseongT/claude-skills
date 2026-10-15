# urimal — 자연스러운 우리말 교정

Korean sentence-editing skill that rewrites translationese in general documents into natural Korean. Runs in Korean; see [README.ko.md](./README.ko.md).

Core idea: translationese isn't wrong grammar — it's English sentence structure left inside Korean. The skill fixes double passives, needless passives, empty light verbs, noun-heavy phrasing, literal English verb calques, and subject–predicate mismatch. Each rule lists what to *keep* as well as what to fix, so it doesn't over-correct natural Korean passives and idioms.

- Triggers: "자연스럽게 고쳐줘", "번역투 빼줘", "우리말답게 바꿔줘", "문장 교정해줘", or any request to polish reports, emails, proposals, papers, blog posts, or translated text.
- Not for: fiction (use [`desoemat`](../desoemat)), spelling-only checks, summaries, or writing from scratch.

MIT — see [LICENSE](../LICENSE).
