# claude-skills

[Claude Code](https://docs.claude.com/en/docs/claude-code) 에서 쓰는 개인용 스킬 모음입니다. 각 스킬은 독립된 디렉터리 안의 `SKILL.md` 한 장으로 동작합니다.

## 스킬 목록

| 스킬 | 한 줄 설명 |
|---|---|
| [`grill-me-p`](./grill-me-p) | 교육 웹서비스·에듀테크 기획을 교육철학자 페르소나로 가혹하게 주관식 검정하는 Pedagogical Grill. |

새 스킬은 이 표에 한 줄 추가합니다.

## 설치

각 스킬 디렉터리를 `~/.claude/skills/` 아래에 그대로 두면 Claude Code 가 자동으로 인식합니다.

```bash
git clone https://github.com/YunseongT/claude-skills.git
cp -r claude-skills/grill-me-p ~/.claude/skills/
```

또는 심볼릭 링크로 두면 레포 업데이트가 바로 반영됩니다.

```bash
ln -s "$(pwd)/claude-skills/grill-me-p" ~/.claude/skills/grill-me-p
```

설치 후 Claude Code 를 재시작하면 `/grill-me-p` 처럼 슬래시 명령으로 호출하거나, 스킬 설명에 적힌 트리거 발화로 자동 호출됩니다.

## 사용

각 스킬은 자신의 `SKILL.md` 상단 frontmatter 의 `description` 에 트리거 조건을 명시합니다. Claude 가 사용자의 발화를 보고 어떤 스킬을 띄울지 라우팅하므로, 슬래시 명령을 외울 필요는 없습니다.

예시:

- `/grill-me-p` 또는 "이 에듀테크 기획 교육적으로 grill 해줘" → `grill-me-p` 호출

## 기여 / 포크

자유롭게 포크해 본인 용도로 고쳐 쓰세요. PR 도 환영합니다. 새 스킬을 추가할 때는:

1. 디렉터리 이름은 kebab-case.
2. `SKILL.md` frontmatter 의 `name`, `description` 은 필수. `description` 에 **언제 호출되어야 하는지** 트리거 발화 예시를 포함합니다.
3. README 의 스킬 목록 표에 한 줄 추가.

## 라이선스

[MIT](./LICENSE). 자유롭게 가져다 쓰시되, 학술적 인용·출처(예: `grill-me-p` 의 Freire, Dewey 등)는 보존하는 것을 권장합니다.
