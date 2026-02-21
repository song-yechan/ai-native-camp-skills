# Block 3: 7개 핵심 기능 — Claude Code의 무기들

> 📖 공식 문서: [Claude Code Docs](https://docs.anthropic.com/en/docs/claude-code)

## EXPLAIN

Claude Code에는 7가지 핵심 기능이 있습니다. 각각의 비유를 기억하세요:

| 기능 | 비유 | 한마디 |
|------|------|--------|
| **CLAUDE.md** | 신입에게 주는 업무 매뉴얼 | 항상 읽는 "나에 대한 설명서" |
| **Skill** | 요리 레시피 | 필요할 때만 꺼내는 반복 업무 |
| **MCP** | USB-C 포트 | 외부 도구 연결 표준 |
| **Subagent** | 부하 직원에게 위임 | 백그라운드 병렬 처리 |
| **Agent Teams** | 프로젝트 TF | 팀원끼리 소통하며 협업 |
| **Hook** | IFTTT / 자동 체크리스트 | 이벤트 기반 자동 실행 |
| **Plugin** | 앱스토어 앱 설치 | 위의 모든 것을 패키지로 |

### 전체 구조도

```
┌─ CLAUDE.md ─── Claude가 매번 읽는 "나에 대한 설명서"  [항상 로딩]
│
├─ Skill ─────── 반복 업무를 저장해둔 "레시피"           [필요할 때 로딩]
│   └─ MCP ───── 외부 도구 연결 "USB 포트"
│
├─ Subagent ──── 백그라운드 처리 (1:1 위임)              [병렬 처리]
│   └─ Agent Teams ── 팀 단위 처리 (N:N 협업)
│
├─ Hook ──────── 이벤트 기반 자동 실행                    [자동화]
│
└─ Plugin ────── 위의 모든 것을 패키지로 묶어 공유        [배포]
```

### CLAUDE.md — "신입사원에게 주는 업무 매뉴얼"

**가장 중요한 기능입니다.**

CLAUDE.md = Claude가 **매 대화 시작 시 자동으로 읽는** 파일
- 프로젝트별: `./CLAUDE.md` — 이 프로젝트에서만 적용
- 전역: `~/.claude/CLAUDE.md` — 모든 프로젝트에 적용

비유: "우리 팀은 이렇게 일해", "나는 이런 스타일을 좋아해", "이건 절대 하지 마"

### Skill — "요리 레시피"

점진적 로딩 (Just-in-time): CLAUDE.md는 항상 로딩, Skill은 **필요할 때만** 로딩

```
.claude/skills/
└── my-skill/
    ├── SKILL.md      (필수 — 레시피 본문)
    ├── scripts/       (자동화 스크립트)
    ├── references/    (참조 자료)
    └── assets/        (이미지 등)
```

### MCP — "USB-C 포트"

AI가 외부 서비스와 대화하는 표준 규약 (Model Context Protocol)

USB-C 하나로 충전기/모니터/외장하드를 다 연결하듯, MCP 하나로 Slack/Notion/Gmail을 다 연결합니다.

### Subagent / Agent Teams — "위임 + 팀 협업"

| 구분 | Subagent | Agent Teams |
|------|----------|-------------|
| 관계 | 1:1 위임 | 팀 프로젝트 |
| 소통 | 보고만 받음 | 팀원 간 소통 가능 |
| 작업 | 독립적 | 공유 태스크 |

### Hook — "IFTTT / 자동 체크리스트"

특정 이벤트가 발생하면 정해진 동작을 확실히 실행하는 결정론적 자동화.

| 이벤트 | 동작 |
|--------|------|
| PreToolUse | 도구 사용 전 체크 |
| PostToolUse | 도구 사용 후 정리 |
| Notification | 알림 보내기 |
| Stop | 세션 종료 시 정리 |

### Plugin — "앱스토어"

Skill + MCP + Hook + Agent 등을 **하나의 설치 단위**로 묶어서 팀 전체가 동일 환경 사용.

## EXECUTE

**CLAUDE.md 만들기 실습**

아래 내용을 Claude에게 요청하세요:
```
CLAUDE.md 파일을 만들어줘. 아래 내용을 포함해줘:
- 사용자 언어: 한국어
- 응답 스타일: 친절하고 간결하게
- 금지 사항: 영어로 답변하지 말 것
```

만들어진 파일 확인:
```bash
cat CLAUDE.md
```

**CLAUDE.md 효과 테스트**

`/clear` 로 새 대화를 시작한 후, Claude에게 아무 질문이나 해보세요. 한국어로 응답하는지 확인합니다.

```
오늘 날씨 어때?
```
→ CLAUDE.md에 "한국어로 답변"이 있으므로 한국어로 응답해야 합니다.

## QUIZ

**Q1. CLAUDE.md의 로딩 방식은?**

```json
{
  "questions": [{
    "question": "CLAUDE.md의 로딩 방식은?",
    "header": "Q1",
    "options": [
      {"label": "사용자가 직접 불러와야 함", "description": "수동 로딩?"},
      {"label": "매 대화 시작 시 자동으로 읽힘", "description": "영구 기억 방식"},
      {"label": "특정 명령어로 호출해야 함", "description": "명령어 기반?"},
      {"label": "한 번 읽으면 더 이상 참조하지 않음", "description": "일회성?"}
    ],
    "multiSelect": false
  }]
}
```
정답: 2번 (매 대화 시작 시 자동으로 읽힘)
해설: CLAUDE.md는 매 세션 시작 시 자동으로 읽히는 "영구 기억"입니다.

**Q2. CLAUDE.md와 Skill의 가장 큰 차이는?**

```json
{
  "questions": [{
    "question": "CLAUDE.md와 Skill의 가장 큰 차이는?",
    "header": "Q2",
    "options": [
      {"label": "파일 형식이 다르다", "description": "형식의 차이?"},
      {"label": "CLAUDE.md는 항상 로딩, Skill은 필요할 때만 로딩", "description": "로딩 시점의 차이"},
      {"label": "Skill이 더 중요하다", "description": "중요도의 차이?"},
      {"label": "CLAUDE.md는 코드만 포함한다", "description": "내용의 차이?"}
    ],
    "multiSelect": false
  }]
}
```
정답: 2번 (CLAUDE.md는 항상 로딩, Skill은 필요할 때만 로딩)
해설: 컨텍스트 윈도우는 유한합니다. CLAUDE.md는 항상, Skill은 필요할 때만 로딩(Just-in-time)합니다.

**Q3. MCP를 USB-C 포트에 비유하는 이유는?**

```json
{
  "questions": [{
    "question": "MCP를 USB-C 포트에 비유하는 이유는?",
    "header": "Q3",
    "options": [
      {"label": "물리적으로 연결해야 해서", "description": "물리적 연결?"},
      {"label": "하나의 표준 규격으로 여러 도구를 연결할 수 있어서", "description": "표준 규격의 힘"},
      {"label": "속도가 빨라서", "description": "속도 때문?"},
      {"label": "유료이기 때문에", "description": "비용 때문?"}
    ],
    "multiSelect": false
  }]
}
```
정답: 2번 (하나의 표준 규격으로 여러 도구를 연결할 수 있어서)
해설: USB-C 하나로 충전기/모니터/외장하드를 다 연결하듯, MCP 하나로 Slack/Notion/Gmail을 다 연결합니다.
