# grill-me-p — Pedagogical Grill

교육 웹서비스·에듀테크 기획을 20년 경력 교육철학자 페르소나로 가혹하게 주관식 검정하는 Claude Code 스킬입니다. 칭찬·공감·완충 표현은 일절 배제하고, 오직 **"이 기획이 교육·인문학적으로 정당한가?"** 만을 학술적 문답으로 압박합니다.

## 무엇을 하는가

기획자의 교육 철학이 실제 UI/UX 구조 위에서 모순 없이 단단해지도록 돕는 **페이스메이커** 역할입니다. 사용자가 학습용 앱·LMS·AI 튜터·학생 대상 서비스의 기획안을 제시하면, 다음 5대 학술 축에서 가장 약한 사각지대를 골라 주관식 한 질문으로 포화합니다.

## 5대 검정축과 출처

| 축 | 개념 | 출처 |
|---|---|---|
| 1 | 지식의 은행 저축식 소외 (Banking Concept), 실천 (Praxis) | Paulo Freire, *Pedagogy of the Oppressed* (1968/70) |
| 2 | 연속적 경험의 축적 (Continuity of Experience) | John Dewey, *Experience and Education* (1938) |
| 3 | 산파술 / 엘렝코스 (Maieutics / Elenchus) | Socrates (Plato 의 초기 대화편) |
| 4 | 가짜 효능감 / 학습 착시 (Illusion of Mastery) | Tom Chatfield 등 디지털 학습 비판 담론 (참고: D. Willingham 의 metacognitive illusion 논의와도 연계됨) |
| 5 | 협력적 주체성 (Collective Agency) | Human-Centered AI in Education / HCAI 담론 (Stanford HAI, UNESCO 'AI and Education' 가이드라인 등) |

### 출처 면책 문구

축 1~3 은 정전(canon)이 확립된 1차 문헌에 직접 기댈 수 있습니다. **축 4 와 5 는 단일 저작이 아니라 동시대 담론 묶음**이며, 위 표에 적힌 이름은 진입점일 뿐 유일하거나 확정적인 권위가 아닙니다. 학술 논문·정식 발표문에 인용하시려면 본 README 의 인용을 출발점으로만 사용하고, 주장하시는 구체적 내용과 일치하는 1차 출처를 직접 확인해 주십시오. 스킬 내부에서 이 이름들은 서지적 권위가 아니라 비판을 거는 **수사적 닻**으로 사용됩니다.

## 발달 단계별 비판 프레임

스킬은 학습자 대상을 먼저 추론한 뒤 비판 수위를 조정합니다.

| 대상 | 1차 인용 프레임 |
|---|---|
| 초등 저학년 | Piaget 전조작기·구체적 조작기, Vygotsky ZPD |
| 초등 고학년~중학생 | 구체적→형식적 조작기 전이, Erikson 정체성 형성 |
| 고등학생 | 형식적 조작기, Kohlberg 후인습 도덕 |
| 대학생·성인 | Mezirow 전환학습, Knowles 안드라고지 |
| 교사·기관 | Shulman PCK, 제도적 책무성 |

## 설치

```bash
# 옵션 A: 복사
cp -r grill-me-p ~/.claude/skills/

# 옵션 B: 심볼릭 링크 (레포 업데이트가 즉시 반영됨)
ln -s "$(pwd)/grill-me-p" ~/.claude/skills/grill-me-p
```

Claude Code 를 재시작하면 인식됩니다.

## 호출

- 슬래시: `/grill-me-p`
- 자동 트리거 (예시):
  - "이 에듀테크 기획 교육적으로 비판해줘"
  - "AI 튜터 UI 흐름 철학적으로 grill 해줘"
  - "학습용 앱 기획 검토해줘"

일반 제품·코드 설계 grill 은 `grill-me-p` 가 아닌 `grill-me` 가 적합합니다.

## 작동 방식 요약

1. **대상 프로파일링** (내부 처리, 출력 없음)
2. **5대 축 중 가장 치명적인 사각지대 1개 포착**
3. **주관식 한 질문 분출** — 한 턴 한 질문, 객관식 보기 없음, 헤더로 어느 축인지 명시
4. **개념어 가로채기 + 비계 유도 재질문** — 답변 속 핵심 단어를 인용해 이상-수단 간 모순을 들이받고, 답을 주는 대신 사용자가 수단을 재설계하도록 유도
5. **종료 조건 충족 시 종합 평가** — 5대 축 중 3개 정렬 / 사용자 요청 / 같은 축 3회 공전

자세한 프롬프트는 [`SKILL.md`](./SKILL.md) 참조.

## 라이선스

리포지터리 루트의 [MIT 라이선스](../LICENSE) 를 따릅니다.
