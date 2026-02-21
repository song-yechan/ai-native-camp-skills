# Block 3: MCP 실습

> 📖 공식 문서: [Claude Code MCP 설정](https://docs.anthropic.com/en/docs/claude-code/mcp)

## EXPLAIN

이제 직접 MCP를 연결하고 사용해보겠습니다.

## EXECUTE

**Step 1: 현재 MCP 상태 확인**

Claude에게 요청하세요:
```
현재 연결된 MCP 서버 목록을 보여줘
```
→ 또는 직접 `/mcp` 입력

**Step 2: MCP 연결하기 (아래 중 하나 선택)**

**옵션 A: Notion MCP (추천)**
```
Notion MCP를 연결해줘
```
→ Claude가 `claude mcp add --transport http notion https://mcp.notion.com/mcp` 실행

**옵션 B: 다른 도구**
사용자에게 AskUserQuestion으로 질문:
```json
{
  "questions": [{
    "question": "어떤 도구를 연결해보고 싶나요?",
    "header": "MCP 선택",
    "options": [
      {"label": "Notion", "description": "문서/DB 연결 (추천)"},
      {"label": "Slack", "description": "채널 메시지 읽기/쓰기"},
      {"label": "Google Calendar", "description": "일정 확인/생성"},
      {"label": "건너뛰기", "description": "개념만 이해하고 넘어가기"}
    ],
    "multiSelect": false
  }]
}
```

**Step 3: 연결 확인**
```
/mcp
```
→ 연결한 도구가 ✅ 상태인지 확인

**Step 4: 연결된 도구 활용 테스트**

Notion을 연결했다면:
```
Notion에서 최근 업데이트된 페이지 3개를 보여줘
```

Calendar를 연결했다면:
```
이번 주 일정을 보여줘
```

> MCP 연결이 어려운 경우, 다음 블록으로 넘어가도 괜찮습니다. 개념 이해가 우선입니다.
