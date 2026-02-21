---
name: day2-context
description: "AI Native Camp Day 2 — 맥락 연결하기: MCP와 Context Sync. '/day2', 'MCP', 'Context Sync' 요청 시 시작."
---

# Day 2: 맥락 연결하기 — MCP와 Context Sync

> **테마**: Context 확장 — 외부 도구의 맥락을 AI에 연결
> **핵심 메시지**: "같은 AI인데 왜 결과가 다를까? 맥락의 유무가 답입니다."
> **예상 소요**: 약 75분
> **사전 과제**: Day 1 CLAUDE.md 작성 완료
> **산출물**: MCP 연결 1개 이상 + Context Sync 스킬 골격

---

## STOP PROTOCOL — 절대 위반 금지

### 각 블록은 반드시 2턴에 걸쳐 진행한다

**Phase A (Turn 1):**
1. 해당 블록의 reference 파일을 **Read tool**로 읽는다
2. `## EXPLAIN` 내용을 설명한다
3. `📖 공식 문서:` URL이 있으면 Phase A 시작 시 표시한다
4. `## EXECUTE` 실습 가이드를 보여준다 (있는 경우)
5. **"직접 실행해보세요! 완료되면 '완료' 또는 '다음'이라고 알려주세요."** 라고 말한다
6. ⛔ **STOP — 여기서 반드시 턴을 종료한다. 사용자 응답을 기다린다.**

**Phase B (Turn 2) — 사용자가 '완료'/'다음' 응답 후:**
1. `## QUIZ` 섹션을 읽는다 (QUIZ가 없는 블록은 바로 다음 블록 안내)
2. **AskUserQuestion** tool로 **1문항씩** 출제한다
3. 정답/오답 피드백을 준다
4. **"다음 블록으로 넘어갈까요?"** 라고 물어본다

### 핵심 금지 사항
1. ❌ Phase A에서 QUIZ를 출제하지 않는다
2. ❌ 한 턴에 EXPLAIN + EXECUTE + QUIZ를 모두 진행하지 않는다
3. ❌ 사용자 응답 없이 다음 블록으로 넘어가지 않는다
4. ❌ reference 파일을 읽지 않고 기억에 의존하여 설명하지 않는다

---

## References 파일 맵

| 블록 | 파일 | QUIZ |
|------|------|------|
| Block 0: 맥락의 중요성 | `references/block0-context-importance.md` | 없음 |
| Block 1: 도구별 설계 철학 | `references/block1-tool-philosophy.md` | 3문항 |
| Block 2: MCP 딥다이브 | `references/block2-mcp-deepdive.md` | 3문항 |
| Block 3: MCP 실습 | `references/block3-mcp-practice.md` | 없음 |
| Block 4: Context Sync 스킬 구축 | `references/block4-context-sync.md` | 3문항 |

---

## 진행 규칙

1. 모든 응답은 **한국어**로 한다
2. 각 블록 시작 시 진행 상태를 표시한다: `📍 Day 2 진행: [Block N/4] — 블록 제목`
3. 사용자가 "자세히", "더 알려줘"라고 하면 reference 파일을 다시 읽어서 상세 설명한다
4. 사용자가 "다음", "넘어가자", "계속"으로 응답하면 다음 블록을 시작한다

---

## 시작

스킬이 호출되면 AskUserQuestion으로 시작 블록을 선택하게 한다:

```json
{
  "questions": [{
    "question": "어느 블록부터 시작할까요?",
    "header": "시작 블록",
    "options": [
      {"label": "Block 0: 맥락의 중요성", "description": "같은 AI, 다른 결과의 비밀 (처음이라면 추천)"},
      {"label": "Block 1: 도구별 설계 철학", "description": "Slack, Gmail, Notion 등의 구조"},
      {"label": "Block 2: MCP 딥다이브", "description": "MCP 작동 원리와 연결 방법"},
      {"label": "Block 3: MCP 실습", "description": "직접 MCP 연결하기"},
      {"label": "Block 4: Context Sync", "description": "여러 도구 맥락을 하나로 수집"}
    ],
    "multiSelect": false
  }]
}
```

---

## 마무리

모든 블록 완료 후 아래를 보여준다:

### 오늘 배운 것 정리

| 개념 | 핵심 |
|------|------|
| 맥락의 중요성 | 같은 AI + 다른 맥락 = 다른 결과 |
| 도구별 설계 철학 | 각 도구의 데이터 구조를 이해하면 AI 활용도 상승 |
| MCP | USB-C 포트처럼 하나의 표준으로 여러 도구 연결 |
| Context Sync | "싱크해줘" 한마디로 여러 도구 맥락을 하나로 |
| Subagent | 병렬 수집으로 시간 절약 |

### 캠프 전체 흐름

```
Day 1: CLAUDE.md = Context 설계     ✅
Day 2: MCP 연결 = Context 확장      ✅ (오늘)
Day 3: 스킬 = Context 활용          (다음)
Day 4: 복리로 키우기 = Context 개선
```

### 산출물
- MCP 연결 1개 이상 (또는 개념 이해)
- Context Sync 스킬 골격

### 다음 시간 예고
**Day 3: 스킬 설계와 제작** — Clarify 프로세스로 모호함을 제거하고, 나만의 스킬을 직접 만듭니다.

> Day 2 완료를 축하합니다! Day 3을 시작하려면 `/day3` 를 입력하세요.
