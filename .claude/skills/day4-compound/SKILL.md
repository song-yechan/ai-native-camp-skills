---
name: day4-compound
description: "AI Native Camp Day 4 — 시스템화: Compound Engineering으로 복리 성장. '/day4', 'Compound', '시스템화' 요청 시 사용."
---

# Day 4: 시스템화 — 만든 걸 복리로 키우는 법

> **테마**: Context Engineering + Compound Engineering
> **핵심 메시지**: "한 번 만들고 끝이 아니다. 쓰면서 고치면 복리로 성장한다."
> **예상 소요**: 약 75분
> **사전 과제**: Day 3 스킬 제작 완료 (또는 시도)
> **산출물**: 개선된 CLAUDE.md + 1주 목표 설정

---

## STOP PROTOCOL — 절대 위반 금지

### 각 블록은 반드시 2턴에 걸쳐 진행한다

**Phase A (Turn 1)**:
1. references/ 에서 해당 블록 파일을 Read
2. EXPLAIN 섹션 내용을 전달
3. EXECUTE 섹션이 있으면 실행
4. **"이 블록의 설명과 실습이 끝났습니다. 이해가 됐으면 '퀴즈 시작'이라고 말씀해주세요."** 출력
5. **STOP — 턴을 종료하고 사용자 응답을 기다린다**

**Phase B (Turn 2)** — 사용자가 퀴즈 진행을 확인한 후:
1. QUIZ 섹션의 문제를 AskUserQuestion으로 출제
2. 정답/오답 피드백 제공
3. "다음 블록으로 넘어갈까요?" 질문

> QUIZ가 없는 블록(Block 2, Block 4)은 Phase A만 진행하고, 완료 후 "다음 블록으로 넘어갈까요?" 질문.

### 핵심 금지 사항
1. Phase A에서 퀴즈를 출제하지 않는다
2. 한 턴에 EXPLAIN + EXECUTE + QUIZ를 모두 진행하지 않는다
3. 사용자 응답 없이 다음 단계로 넘어가지 않는다
4. references 파일을 Read하지 않고 기억에 의존하여 설명하지 않는다

---

## References 파일 맵

| Block | 파일 | QUIZ |
|-------|------|------|
| Block 0: Context Engineering | `references/block0-context-engineering.md` | 3문항 |
| Block 1: Compound Engineering | `references/block1-compound-engineering.md` | 3문항 |
| Block 2: GitHub 기초 | `references/block2-github-basics.md` | 없음 |
| Block 3: 서비스화 | `references/block3-service.md` | 3문항 |
| Block 4: Compound 사이클 실습 | `references/block4-compound-practice.md` | 없음 |

---

## 진행 규칙

1. 각 블록 시작 시: `📍 Day 4 진행: [Block N/4] — 블록 제목`
2. 사용자가 "다음", "넘어가자", "계속" → 다음 블록 시작
3. 사용자가 "자세히", "더 알려줘" → 해당 reference 파일의 상세 내용 전달
4. 모든 응답은 한국어

---

## 시작

아래 AskUserQuestion으로 시작 블록을 선택받는다:

```json
{
  "questions": [{
    "question": "Day 4를 어디서부터 시작할까요?",
    "header": "시작 블록",
    "options": [
      {"label": "Block 0부터 (처음부터)", "description": "Context Engineering부터 순서대로"},
      {"label": "Block 1: Compound Engineering", "description": "복리 성장 개념부터"},
      {"label": "Block 2: GitHub 기초", "description": "버전 관리부터"},
      {"label": "Block 4: 실습 바로 시작", "description": "이론 건너뛰고 실습부터"}
    ],
    "multiSelect": false
  }]
}
```

---

## 마무리

모든 블록 완료 후:

### 오늘 배운 것 정리

| 개념 | 핵심 |
|------|------|
| Context Engineering | 프롬프트가 아니라 **맥락을 설계**하는 것 |
| Compound Engineering | 쓰면서 고치면 **복리로 성장** |
| 풀 사이클 | Build → Use → Notice → Debug → Fix → Document |
| GitHub 기초 | Repository, Commit, Branch, PR — **기록의 인프라** |
| 서비스화 | GitHub + Vercel + Supabase로 스킬을 서비스로 확장 |

### 4일간의 여정 요약

```
Day 1: CLAUDE.md     = Context 설계     ✅
Day 2: MCP 연결      = Context 확장     ✅
Day 3: 스킬 제작     = Context 활용     ✅
Day 4: 복리로 키우기 = Context 개선     ✅ (오늘)
```

### 산출물 확인
- [ ] 개선된 CLAUDE.md (새 규칙 추가)
- [ ] 1주 목표 설정 완료

### 1주일 동안 할 일
1. **만든 것 실제로 써보기** — CLAUDE.md, 스킬을 실제 업무에 적용
2. **불편한 점 발견하면 고치기** — Compound Engineering 사이클 반복
3. **최종 발표 준비** — 동작하는 영상 또는 링크 준비

### 핵심 메시지

> "4일 동안 세 가지를 만들었습니다.
> CLAUDE.md, MCP 연결, 스킬.
>
> 오늘 배운 건 이것들을 **내 마음에 들게** 만드는 법입니다.
>
> 쓰고, 고치고, 쌓으세요.
> **그게 복리입니다.**"

AI Native Camp 4일 과정을 모두 완료했습니다!
1주 후 최종 발표에서 여러분의 결과물을 기대합니다.
