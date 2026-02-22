# Block 3-2: Skill — 반복 작업 레시피

> **Phase A 시작 시 반드시 아래 형태로 출력한다:**
> ```
> 📖 공식 문서: https://code.claude.com/docs/ko/skills
> ```

## EXPLAIN

| 항목 | 내용 |
|------|------|
| 비유 | 요리 레시피 — 필요할 때만 꺼내는 반복 업무 자동화 |
| 핵심 | CLAUDE.md는 항상 로딩, Skill은 **필요할 때만** 로딩 (Just-in-time) |
| 호출 | `/스킬이름`으로 호출하면 Claude가 레시피대로 실행 |

### CLAUDE.md vs Skill 차이

```
CLAUDE.md  → 매 세션 시작 시 항상 로딩  (영구 기억)
Skill      → /스킬이름 호출할 때만 로딩  (필요할 때)
```

왜 나눌까? → **컨텍스트 윈도우는 유한**하기 때문. 항상 필요한 건 CLAUDE.md에, 가끔 필요한 건 Skill에 넣는다.

### 스킬 파일 구조

```
.claude/skills/
└── my-skill/
    ├── SKILL.md      (필수 — 레시피 본문)
    ├── scripts/       (자동화 스크립트)
    ├── references/    (참조 자료)
    └── assets/        (이미지 등)
```

## EXECUTE

아래를 Claude에게 요청해보세요:

```
내가 설치한 스킬 목록을 보여줘
```

그리고 이 캠프 스킬이 어떤 구조인지 확인:

```
.claude/skills/ 폴더 구조를 보여줘
```

> Day 3에서 직접 스킬을 만들어봅니다. 지금은 구조만 파악하면 됩니다.
