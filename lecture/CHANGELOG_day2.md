# Day 2 강의 가이드 변경사항

## 변경된 슬라이드/섹션 목록

### 1. Day 1 리마인드 슬라이드
- Subagent: "백그라운드에서 처리" → "독립 컨텍스트에서 처리"

### 2. MCP 연결 방법 3가지 슬라이드
- **변경 전**: "방법 1: Connectors (가장 쉬움)"
- **변경 후**: "방법 1: claude.ai 웹 설정 (가장 쉬움)" + "Claude Code에서 자동으로 사용 가능" 추가
- 발표자 노트: "Connectors" → "claude.ai 웹 설정"

### 3. Connectors로 연결하기 슬라이드 → 제목 변경
- **변경 전**: "Connectors로 연결하기 (방법 1)"
- **변경 후**: "claude.ai 웹 설정으로 연결하기 (방법 1)"
- "5️⃣ 연결 완료!" 아래에 "→ Claude Code에서 자동으로 사용 가능" 추가

### 4. 명령어로 연결하기 슬라이드
- **변경 전**: `claude mcp add slack`
- **변경 후**: Slack은 "claude.ai/settings/connectors에서 연결 추천"으로 변경

### 5. MCP 실습 1 (Slack 연결) 슬라이드
- "Connectors로 Slack 연결" → "claude.ai 웹 설정으로 Slack 연결"

### 6. MCP 실습 2 (Notion 연결) 슬라이드
- "Connectors로 Notion 연결" → "claude.ai 웹 설정으로 Notion 연결"

### 7. MCP 관리 명령어 슬라이드
- **변경 전**: "Lazy Loading" 설정 설명
- **변경 후**: "Tool Search" 기능으로 변경 — "MCP 도구가 많으면 자동으로 필요할 때만 로딩 (컨텍스트의 10% 이상 차지 시 자동 활성화)"

### 8. MCP 핵심 정리 슬라이드
- "Connectors — 클릭만으로 연결" → "claude.ai 웹 설정 — 클릭만으로 연결"
- "명령어 — claude mcp add" → "명령어 — claude mcp add --transport http"

### 9. Block 5 (Context Sync 완성) 슬라이드
- **변경 전**: "트리거 확인" + `triggers:` frontmatter
- **변경 후**: "스킬 설정 확인" + `description:` 키워드 통합 방식으로 변경

### 10. 오늘 배운 것 슬라이드
- "Connectors / 명령어 / .mcp.json" → "claude.ai 웹 설정 / 명령어 / .mcp.json"

### 11. 도구별 설계 철학 상세 (전체)
- 모든 도구의 "MCP 연결: Connectors" → "MCP 연결: claude.ai 웹 설정"으로 통일 (Slack, Notion, Drive, Linear 등)
- "Lazy Loading" → "Tool Search" 용어 수정

### 12. Context Sync 스킬 상세 정리
- `triggers:` 필드 → `description:` 키워드 통합 방식으로 변경
- `claude mcp add slack` 삭제

### 13. 실습 가이드 (MCP 연결)
- "Connectors로 Slack/Notion 연결" → "claude.ai 웹 설정으로 Slack/Notion 연결"
