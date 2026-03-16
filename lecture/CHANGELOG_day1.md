# Day 1 강의 가이드 변경사항

## 변경된 슬라이드/섹션 목록

### 1. 사전 과제 (개요 테이블)
- **변경 전**: "Claude Pro/Max/Teams 구독"
- **변경 후**: "Claude Pro/Max/Teams/Enterprise 구독"

### 2. 설치 확인 슬라이드
- **변경 전**: "✅ 구독 확인: Claude Pro ($20/월) 이상 필요"
- **변경 후**: "✅ 구독 확인: Claude Pro/Max/Teams/Enterprise 구독 필요 (무료 플랜은 Claude Code 사용 불가)"

### 3. 7대 기능 전체 구조 (Block 3 소개 슬라이드)
- **변경 전**: "Subagent ──── 백그라운드에서 처리" / "Agent Teams ── 여러 명한테 동시에 일 시키기"
- **변경 후**: "Subagent ──── 독립 컨텍스트에서 처리" / "Agent Teams ── 여러 명한테 동시에 일 시키기 (실험적 기능)"

### 4. MCP 소개 슬라이드 (Block 3-3)
- **변경 전**: `claude mcp add notion https://mcp.notion.com/mcp`
- **변경 후**: `claude mcp add --transport http notion https://mcp.notion.com/mcp`

### 5. Subagent 슬라이드 (Block 3-4)
- **변경 전**: "팀원한테 일 맡기기 (백그라운드에서 처리)"
- **변경 후**: "팀원한테 일 맡기기 (독립 컨텍스트에서 처리)"
- 발표자 노트: "긴 작업을 백그라운드에서 처리" → "독립적인 컨텍스트에서 작업을 위임"

### 6. Agent Teams 슬라이드 (Block 3-5)
- **변경 전**: "3-5 Agent Teams"
- **변경 후**: "3-5 Agent Teams (실험적 기능)"

### 7. Hook 이벤트 테이블 (Block 3-6)
- **변경 전**: Stop = "세션 종료 시 정리" (4개 이벤트만)
- **변경 후**: Stop = "Claude 응답 완료 시 실행" + "그 외 다수 (SessionStart, SubagentStart 등)" 행 추가

### 8. Plugin 비유 슬라이드 (Block 3-7)
- **변경 전**: `claude plugin add ← 한줄`
- **변경 후**: `/plugin install ← 한줄`

### 9. 7대 기능 요약 슬라이드
- Subagent: "백그라운드 처리" → "독립 컨텍스트 처리"
- Agent Teams: "(N:N)" → "(N:N, 실험적)"

### 10. 비유 모음 테이블
- Agent Teams: "팀원들이 서로 소통하며 협업" → "팀원들이 서로 소통하며 협업 (실험적)"

### 11. 참고 자료 URL
- **변경 전**: `https://code.claude.com/docs/en/mcp` (영문)
- **변경 후**: `https://code.claude.com/docs/ko/mcp` (한국어)
