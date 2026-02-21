# Block 4: Compound 사이클 실습 + 마무리

## EXPLAIN

이제 직접 Compound Engineering 사이클을 한 바퀴 돌려봅니다.

**오늘 할 일은 딱 하나: 사이클을 한 바퀴 돌리는 것.**

## EXECUTE

### 실습 A: CLAUDE.md 규칙 추가 (필수, 15분)

**Step 1: Notice (불편함 발견) — 3분**

사용자에게 AskUserQuestion으로 질문:

```json
{
  "questions": [{
    "question": "Day 1~3 동안 Claude에게 매번 반복해서 말한 것이 있었나요? (예: 한국어로 답해줘, 표로 정리해줘, 존댓말로 해줘 등)",
    "header": "반복 패턴",
    "options": [
      {"label": "응답 언어/스타일", "description": "한국어, 존댓말, 이모지 등"},
      {"label": "출력 형식", "description": "표, 목록, 코드블록 등"},
      {"label": "작업 방식", "description": "확인 후 진행, 단계별 등"},
      {"label": "직접 입력", "description": "다른 반복 패턴을 직접 설명"}
    ],
    "multiSelect": false
  }]
}
```

**Step 2: Debug (원인 파악) — 2분**

```
💡 왜 매번 말해야 했을까요?
→ CLAUDE.md에 해당 규칙이 없었기 때문입니다!
```

**Step 3: Fix (규칙 추가) — 5분**

Claude에게 요청:
```
CLAUDE.md에 다음 규칙을 추가해줘: [사용자가 답변한 반복 내용]
```

**Step 4: Document (기록) — 2분**
```
방금 추가한 규칙이 뭔지 CLAUDE.md에서 확인해줘
```

**Step 5: 효과 확인 — 3분**

`/clear` 로 새 대화를 시작한 후, 아무 질문이나 해서 규칙이 적용되는지 확인합니다.

```
🎉 축하합니다! 사이클을 한 바퀴 돌렸습니다.
   여러분은 이미 Compound Engineering을 하고 있습니다.
```

---

### 실습 B: 스킬 출력 수정 (선택, 5분)

Day 3에서 만든 스킬이 있다면:

1. **Use** — 스킬 실행
2. **Notice** — 출력 중 마음에 안 드는 부분 발견
3. **Fix** — "이 스킬의 출력 포맷을 [원하는 형식]으로 바꿔줘"
4. **Use Again** — 수정된 결과 확인

---

### 1주 목표 설정

사용자에게 AskUserQuestion으로 질문:

```json
{
  "questions": [{
    "question": "1주일 후 최종 발표에서 보여줄 목표를 설정해주세요. 템플릿: '1주일 후, 나는 [____]를 보여줄 수 있다'",
    "header": "1주 목표",
    "options": [
      {"label": "스킬 자동화", "description": "한 가지 업무가 스킬로 자동화된다"},
      {"label": "워크플로우 완성", "description": "MCP + 스킬이 연결된 워크플로우가 동작한다"},
      {"label": "서비스 프로토타입", "description": "다른 사람도 쓸 수 있는 웹 서비스가 있다"},
      {"label": "직접 입력", "description": "나만의 목표를 직접 설명"}
    ],
    "multiSelect": false
  }]
}
```

**목표 작성 가이드:**
- 구체적으로: "주간 업무 요약 스킬이 Slack + Gmail 데이터를 가져온다"
- 측정 가능하게: "동작하는 영상을 녹화할 수 있다"
- 현실적으로: "한 가지 업무가 자동화된다"

**목표 기록:**

사용자 답변을 받은 후:
```
CLAUDE.md에 '1주 목표' 섹션을 추가해줘.
목표: [사용자 답변]
```
