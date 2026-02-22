# Block 2: MCP 딥다이브

> **Phase A 시작 시 반드시 아래 형태로 출력한다:**
> ```
> 📖 공식 문서: https://code.claude.com/docs/ko/mcp
> 📖 MCP 프로토콜: https://modelcontextprotocol.io
> ```

## EXPLAIN

### MCP (Model Context Protocol) = AI가 외부 서비스와 대화하는 표준 규약

**비유: USB-C 포트**
- 옛날: 기기마다 다른 포트 → 전용 케이블 필요
- 지금: USB-C 하나로 다 연결
- MCP: 도구마다 다른 API → MCP라는 **표준 규격**으로 통일

### 작동 방식

```
사용자: "Slack에서 #general 메시지 읽어줘"
    ↓
Claude → MCP 프로토콜 → Slack MCP 서버 → Slack API → 결과 반환
    ↓
Claude: "최근 메시지 10개입니다: ..."
```

핵심:
- Claude는 MCP 프로토콜만 알면 됨
- 각 도구의 API 세부사항은 MCP 서버가 처리
- 사용자는 자연어로 요청만 하면 됨

### 연결 방법 3가지

| 방법 | 난이도 | 설명 |
|------|--------|------|
| **Connectors** | 쉬움 (추천) | claude.ai/settings/connectors에서 클릭으로 연결 |
| **명령어** | 보통 | `claude mcp add slack` 한 줄 |
| **수동 설정** | 어려움 | `.mcp.json` 파일 직접 편집 |

### 확인 및 관리

```
/mcp                              # 연결 상태 확인
claude mcp disable [서버명]        # 비활성화
claude mcp enable [서버명]         # 다시 활성화
```

### 컨텍스트 관리 팁

MCP 도구가 많으면 컨텍스트 토큰을 많이 소비합니다.

- ✅ 자주 쓰는 도구만 연결
- ✅ `/mcp`로 연결 상태 주기적 확인
- ✅ 문제 있으면 disable → 다시 enable
- ❌ 모든 도구를 한꺼번에 연결
- ❌ 사용하지 않는 연결 방치

## QUIZ

**Q1. MCP의 역할은?**

```json
{
  "questions": [{
    "question": "MCP의 역할은?",
    "header": "Q1",
    "options": [
      {"label": "AI 모델을 학습시키는 것", "description": "모델 학습?"},
      {"label": "AI가 외부 서비스와 대화하는 표준 규약", "description": "표준 통신 프로토콜"},
      {"label": "데이터를 암호화하는 것", "description": "보안?"},
      {"label": "파일을 압축하는 것", "description": "압축?"}
    ],
    "multiSelect": false
  }]
}
```
정답: 2번 (AI가 외부 서비스와 대화하는 표준 규약)
해설: MCP = Model Context Protocol, AI가 외부 도구와 통신하는 표준 규격입니다.

**Q2. MCP 연결에서 가장 쉬운 방법은?**

```json
{
  "questions": [{
    "question": "MCP 연결에서 가장 쉬운 방법은?",
    "header": "Q2",
    "options": [
      {"label": ".mcp.json 수동 편집", "description": "직접 파일 편집"},
      {"label": "API 키 직접 입력", "description": "API 키 관리"},
      {"label": "Connectors (클릭으로 연결)", "description": "웹에서 클릭만으로"},
      {"label": "코드 작성", "description": "코드 필요?"}
    ],
    "multiSelect": false
  }]
}
```
정답: 3번 (Connectors)
해설: claude.ai/settings/connectors에서 버튼 클릭만으로 연결할 수 있습니다.

**Q3. MCP 연결 상태를 확인하는 명령어는?**

```json
{
  "questions": [{
    "question": "MCP 연결 상태를 확인하는 명령어는?",
    "header": "Q3",
    "options": [
      {"label": "/help", "description": "도움말?"},
      {"label": "/status", "description": "상태 확인?"},
      {"label": "/mcp", "description": "MCP 전용 확인 명령어"},
      {"label": "/connect", "description": "연결 명령어?"}
    ],
    "multiSelect": false
  }]
}
```
정답: 3번 (/mcp)
해설: /mcp 명령어로 현재 연결된 MCP 서버와 사용 가능한 도구를 확인합니다.
