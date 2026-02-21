---
name: day2-context
description: "AI Native Camp Day 2 — 맥락 연결하기: MCP와 Context Sync. '/day2', 'MCP', 'Context Sync' 요청 시 사용."
---

# Day 2: 맥락 연결하기 — MCP와 Context Sync

> **테마**: Context 확장 — 외부 도구의 맥락을 AI에 연결
> **핵심 메시지**: "같은 AI인데 왜 결과가 다를까? 맥락의 유무가 답입니다."
> **예상 소요**: 약 75분
> **사전 과제**: Day 1 CLAUDE.md 작성 완료
> **산출물**: MCP 연결 1개 이상 + Context Sync 스킬 골격

---

## 진행 가이드 (Claude가 따를 지시)

### 인터랙션 규칙
1. **한 블록씩 순서대로** 진행한다. 블록을 건너뛰지 않는다.
2. 각 블록의 **EXPLAIN → EXECUTE → QUIZ** 순서를 지킨다 (없는 단계는 생략).
3. EXPLAIN은 **핵심 비유와 개념만 압축**해서 전달한다. 상세 내용은 "references/concepts.md 참조"로 안내한다.
4. EXECUTE는 사용자가 **직접 따라할 수 있도록** 구체적 명령어와 기대 결과를 보여준다.
5. QUIZ는 **AskUserQuestion** tool로 객관식 3문항을 출제한다. 정답 시 다음 블록, 오답 시 해설 후 재시도.
6. 각 블록 완료 후 **"다음 블록으로 넘어갈까요?"** 라고 물어보고 사용자 응답을 기다린다.
7. 모든 응답은 **한국어**로 한다.
8. 사용자가 "다음", "넘어가자", "계속" 등으로 응답하면 다음 블록을 시작한다.
9. 사용자가 "자세히", "더 알려줘" 라고 하면 references/concepts.md의 해당 섹션을 읽어서 상세 설명한다.

### 진행 상태 표시
각 블록 시작 시 아래 형식으로 진행 상태를 보여준다:
```
📍 Day 2 진행: [Block N/5] — 블록 제목
```

---

## Block 0: 맥락의 중요성

### EXPLAIN

📍 Day 2 진행: [Block 0/5] — 맥락의 중요성

**같은 AI인데, 왜 결과가 다를까?**

예시: "다음 주 미팅 안건 만들어줘"

**맥락 없이 물으면:**
> 1. 진행 상황 업데이트 2. 이슈 논의 3. 다음 계획
→ 어떤 팀에나 동일한 뻔한 결과

**6개 도구가 연결된 AI에게 물으면:**
> - [Linear] 스프린트 8 완료율 72%, 블로커 2건
> - [Slack] #product에서 결제 UX 논의 미결
> - [Gmail] 고객사 A SLA 회신 대기 3일째
> - [Calendar] 수요일 디자인 리뷰 → 시안 사전 공유 필요

→ **나만의 상황**에 맞는 구체적 안건이 나옵니다.

**문제**: 이 맥락을 매번 복사-붙여넣기? → 5분이면 지쳐서 결국 안 하게 됨

**해법**:
- **MCP** = 도구를 AI에 직접 연결 (자동으로 맥락 수집)
- **Context Sync 스킬** = "싱크해줘" 한마디로 여러 도구 맥락을 한 문서로 정리

> 상세 내용은 `references/concepts.md` 섹션 5를 참조하세요.

---

## Block 1: 도구별 설계 철학

### EXPLAIN

📍 Day 2 진행: [Block 1/5] — 도구별 설계 철학

도구마다 **데이터를 구조화하는 방식**이 다릅니다. 이 구조를 이해하면 AI가 더 정확하게 활용합니다.

**맥락의 지도:**

| 카테고리 | 도구 | 핵심 설계 철학 | AI가 읽는 맥락 |
|---------|------|--------------|--------------|
| 소통 | **Slack** | 투명한 채널 기반 소통 | 채널=경계선, 스레드=깊이 |
| 소통 | **Gmail** | 정리하지 말고 검색하라 | 라벨=메타데이터, 스레드=기록 |
| 지식 | **Notion** | Everything is a Block | 블록=구조화 데이터, DB=쿼리 |
| 지식 | **Drive** | 파일 공유 + 공동 편집 | 축적된 산출물 아카이브 |
| 실행 | **Linear** | 애자일 방법론 구현 | 이슈=실행 상태 |
| 실행 | **Calendar** | 미래의 시간 자원 구조화 | 이벤트=미래의 구조 |

**Calendar의 특별함:**
> 다른 모든 도구는 과거와 현재를 담지만, Calendar만 **미래**를 담는다.
> → 크로스 도구 검색의 **시작점**이 된다.

> 상세 내용은 `references/concepts.md` 섹션 1을 참조하세요.

### QUIZ

**Q1. Slack에서 AI가 맥락을 읽는 구조는?**
- (A) 파일과 폴더
- (B) 채널(경계선)과 스레드(깊이) ✅
- (C) 페이지와 블록
- (D) 라벨과 필터

해설: Slack은 채널이 맥락의 경계선, 스레드가 맥락의 깊이를 나타냅니다.

**Q2. Gmail의 설계 철학 "Search, not Sort"가 의미하는 것은?**
- (A) 이메일을 정렬하라
- (B) 폴더에 정리하지 말고 검색으로 찾으라 ✅
- (C) 이메일을 삭제하라
- (D) 라벨을 사용하지 말라

해설: Gmail은 용량을 늘려 "절대 삭제하지 마라, 검색으로 찾아라"라는 패러다임을 만들었습니다.

**Q3. 다른 도구와 달리 Calendar만 담고 있는 정보는?**
- (A) 과거의 기록
- (B) 현재의 상태
- (C) 미래의 구조 ✅
- (D) 파일의 버전

해설: Calendar만 미래를 담으므로, 크로스 도구 검색의 시작점이 됩니다.

---

## Block 2: MCP 딥다이브

### EXPLAIN

📍 Day 2 진행: [Block 2/5] — MCP 딥다이브

**MCP (Model Context Protocol) = AI가 외부 서비스와 대화하는 표준 규약**

**비유: USB-C 포트**
- 옛날: 기기마다 다른 포트 → 전용 케이블 필요
- 지금: USB-C 하나로 다 연결
- MCP: 도구마다 다른 API → MCP라는 **표준 규격**으로 통일

**작동 방식:**
```
사용자: "Slack에서 #general 메시지 읽어줘"
    ↓
Claude → MCP 프로토콜 → Slack MCP 서버 → Slack API → 결과 반환
    ↓
Claude: "최근 메시지 10개입니다: ..."
```

**연결 방법 3가지:**

| 방법 | 난이도 | 설명 |
|------|--------|------|
| **Connectors** | 쉬움 (추천) | claude.ai/settings/connectors에서 클릭으로 연결 |
| **명령어** | 보통 | `claude mcp add slack` 한 줄 |
| **수동 설정** | 어려움 | `.mcp.json` 파일 직접 편집 |

**확인 명령어:** `/mcp`

> 상세 내용은 `references/concepts.md` 섹션 2를 참조하세요.

### QUIZ

**Q1. MCP의 역할은?**
- (A) AI 모델을 학습시키는 것
- (B) AI가 외부 서비스와 대화하는 표준 규약 ✅
- (C) 데이터를 암호화하는 것
- (D) 파일을 압축하는 것

해설: MCP = Model Context Protocol, AI가 외부 도구와 통신하는 표준 규격입니다.

**Q2. MCP 연결에서 가장 쉬운 방법은?**
- (A) .mcp.json 수동 편집
- (B) API 키 직접 입력
- (C) Connectors (클릭으로 연결) ✅
- (D) 코드 작성

해설: claude.ai/settings/connectors에서 버튼 클릭만으로 연결할 수 있습니다.

**Q3. MCP 연결 상태를 확인하는 명령어는?**
- (A) /help
- (B) /status
- (C) /mcp ✅
- (D) /connect

해설: /mcp 명령어로 현재 연결된 MCP 서버와 사용 가능한 도구를 확인합니다.

---

## Block 3: MCP 실습

### EXPLAIN

📍 Day 2 진행: [Block 3/5] — MCP 실습

이제 직접 MCP를 연결하고 사용해보겠습니다.

### EXECUTE

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
- "어떤 도구를 연결해보고 싶나요? (Slack / Notion / Google Calendar / 기타)"

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

---

## Block 4: Context Sync 스킬 구축

### EXPLAIN

📍 Day 2 진행: [Block 4/5] — Context Sync 스킬 구축

**Context Sync** = 여러 도구에서 정보를 자동 수집하여 하나의 문서로 정리하는 스킬

**Before**: 매일 아침 30분 — Slack → Gmail → Calendar → Notion 하나씩 열어서 확인
**After**: "싱크해줘" → 1분 후 오늘의 컨텍스트가 하나의 문서로 정리

**직종별 추천 도구 조합:**

| 직종 | 추천 조합 |
|------|----------|
| PM/기획자 | Slack + Linear + Calendar |
| 마케터 | Slack + Gmail + 소셜미디어 |
| 영업 | Gmail + Calendar + CRM |
| CEO/리더 | Slack + Calendar + 뉴스 |

> 상세 내용은 `references/concepts.md` 섹션 3~4를 참조하세요.

### EXECUTE

**Step 1: 도구 선택**

사용자에게 AskUserQuestion으로 질문:
- "Context Sync에 포함할 도구를 선택해주세요 (복수 선택 가능): Slack / Notion / Gmail / Calendar / Linear / 기타"

**Step 2: 스킬 골격 생성**

Claude에게 요청:
```
지금 선택한 도구들로 Context Sync 스킬 골격을 만들어줘.
.claude/skills/my-context-sync/SKILL.md 에 저장해줘.
```

기대 결과:
```
.claude/skills/my-context-sync/
├── SKILL.md          # 스킬 본체
└── references/       # 참고 문서
```

**Step 3: SKILL.md 확인**
```
만들어진 SKILL.md 내용을 보여줘
```

확인할 것:
- frontmatter (`name`, `description`) 존재
- 소스 정의 (어떤 도구에서 수집할지)
- 실행 흐름 (수집 → 통합 → 저장)
- 출력 형식 (md 파일)

**Step 4: 테스트 실행 (MCP가 연결된 경우)**
```
방금 만든 Context Sync 스킬을 실행해줘
```
→ 결과물이 파일로 저장되는지 확인

> MCP가 연결되지 않았더라도, 스킬 골격을 만드는 것 자체가 학습입니다.

### QUIZ

**Q1. Context Sync 스킬의 핵심 가치는?**
- (A) 코드를 자동으로 작성해주는 것
- (B) 여러 도구의 맥락을 하나의 문서로 자동 정리하는 것 ✅
- (C) 파일을 자동으로 백업하는 것
- (D) 이메일을 자동으로 보내는 것

해설: Context Sync는 여러 도구의 맥락을 수집하여 하나의 문서로 정리합니다.

**Q2. Subagent를 활용하면 좋은 이유는?**
- (A) 비용이 절감된다
- (B) Slack, Notion, Calendar를 동시에 수집할 수 있다 (병렬 처리) ✅
- (C) 결과가 더 정확해진다
- (D) 보안이 강화된다

해설: 각 도구의 수집은 서로 의존성이 없으므로, Subagent로 병렬 수집하면 시간이 절약됩니다.

**Q3. 스킬의 출력 형식으로 가장 기본적인 것은?**
- (A) PDF 파일
- (B) 엑셀 파일
- (C) Markdown(.md) 파일 ✅
- (D) 이미지 파일

해설: Markdown 파일이 가장 기본이고 범용적입니다. 이후 Slack 메시지나 Notion 페이지로 확장 가능합니다.

---

## Block 5: 마무리

### EXPLAIN

📍 Day 2 진행: [Block 5/5] — 마무리

### 오늘 배운 것 정리

| 개념 | 핵심 |
|------|------|
| 맥락의 중요성 | 같은 AI + 다른 맥락 = 다른 결과 |
| 도구별 설계 철학 | 각 도구의 데이터 구조를 이해하면 AI 활용도 상승 |
| MCP | USB-C 포트처럼 하나의 표준으로 여러 도구 연결 |
| Context Sync | "싱크해줘" 한마디로 여러 도구 맥락을 하나로 |
| Subagent | 병렬 수집으로 시간 절약 |

### 오늘의 산출물
- MCP 연결 1개 이상 (또는 개념 이해)
- Context Sync 스킬 골격 (`my-context-sync/SKILL.md`)

### 캠프 전체 흐름에서의 위치
```
Day 1: CLAUDE.md = Context 설계     ✅
Day 2: MCP 연결 = Context 확장      ✅ (오늘)
Day 3: 스킬 = Context 활용          (다음)
Day 4: 복리로 키우기 = Context 개선
```

### 다음 시간 예고
**Day 3: 스킬 설계와 제작** — Clarify 프로세스로 모호함을 제거하고, 나만의 스킬을 직접 만듭니다.

> Day 2 완료를 축하합니다! 🎉
> Day 3을 시작하려면 `/day3` 를 입력하세요.
