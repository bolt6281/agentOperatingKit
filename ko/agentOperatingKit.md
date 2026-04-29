# AOK 템플릿 팩

이 파일은 실제 agent 지침 파일이 아니다. Agent Operating Kit(AOK)를 새 프로젝트나 기존 프로젝트에 적용할 때 참고하는 원본 인덱스다.

AOK는 더 큰 프롬프트를 만들기 위한 도구가 아니라, 항상 읽는 agent 지침은 작게 유지하고 필요한 workflow와 프로젝트 지식만 찾아 읽게 만드는 템플릿 팩이다.

실제 적용 시에는 이 파일을 그대로 복사하지 말고, 필요한 문서만 아래 순서로 읽고 사용자가 선택한 항목만 프로젝트에 반영한다.

English version: [../en/agentOperatingKit.md](../en/agentOperatingKit.md)

## 읽는 순서

1. [AOK 적용 가이드라인](aok/application-guide.md)
2. [구성요소 선택 가이드](aok/component-selection.md)
3. [권장 파일 구조](aok/file-structure.md)
4. workflow를 적용할 경우 [Superpowers 설치 및 workflow 적용 전제](aok/superpowers-install.md)
5. 필요한 템플릿 또는 workflow 파일만 선택해서 읽는다.

## 기본 원칙

- 루트 `AGENTS.md`는 매 세션 읽어도 부담 없는 크기로 유지한다. 작은 프로젝트는 50-100줄 안팎을 우선한다.
- `AGENTS.md`에는 항상 읽혀도 손해가 적은 핵심 지침만 둔다.
- 긴 절차는 `.agents/workflows/*.md`로 분리하고, 필요할 때만 읽게 한다.
- 하위 `AGENTS.md`는 자동 생성하지 않는다. 반복적이고 범위가 명확한 규칙만 사용자 승인 후 만든다.
- agent 지침 파일 자체는 관리 대상 정책 파일로 취급한다.
- 파일명은 기본적으로 대문자 `AGENTS.md`를 사용한다.
- `~/.codex/AGENTS.md`는 사용자가 이미 정한 전역 지침이 있을 수 있으므로 기본 적용 대상에서 제외하고, 사용자가 선택한 경우에만 제안한다.
- AOK 적용은 선택지형 인터뷰, 적용안 제안, 사용자 승인 후 반영 순서로 진행한다.
- workflow 템플릿은 Superpowers 설치 환경을 기준으로 한다. Superpowers를 쓰지 않는 프로젝트에는 `.agents/workflows/*.md`를 제공하지 않고 루트 `AGENTS.md`의 기본 작업 원칙만 적용한다.

AOK 적용의 성공 기준은 일반 작업에서 agent가 읽어야 하는 기본 컨텍스트가 줄어드는 것이다. AOK를 적용한 결과 모든 작업에서 더 많은 문서를 기본으로 읽게 된다면 적용이 잘못된 것이다.

## 읽는 빈도 모델

고정된 도입 단계가 아니라 읽는 빈도를 기준으로 문서를 나눈다.

| 빈도 | 파일 | 규칙 |
|---|---|---|
| 항상 읽음 | 루트 `AGENTS.md` | 매 세션 읽어도 부담 없게 짧게 유지 |
| 라우팅 시 읽음 | `.agents/INDEX.md`, 하위 `AGENTS.md` | 작업이 해당 영역에 들어가거나 라우팅이 필요할 때만 읽음 |
| 작업별로 읽음 | 선택된 `.agents/workflows/*.md` | 해당 반복 작업에만 읽음 |
| 참조가 필요할 때 읽음 | ADR, current status, version history | 작업이 해당 기준 문서에 의존할 때만 읽음 |
| 예외 상황에 읽음 | work log, archive | 롤백, 복구, 장애 조사, 회귀 추적, 과거 보존 확인 때만 읽음 |

## 템플릿

| 목적 | 파일 |
|---|---|
| 전역 Codex 지침 | [aok/templates/global-agents.md](aok/templates/global-agents.md) |
| repo 루트 `AGENTS.md` | [aok/templates/repo-agents.md](aok/templates/repo-agents.md) |
| 문서 지도 섹션 | [aok/templates/document-map.md](aok/templates/document-map.md) |
| agent 지침 거버넌스 섹션 | [aok/templates/agent-instruction-governance.md](aok/templates/agent-instruction-governance.md) |
| `.agents/INDEX.md` | [aok/templates/agents-index.md](aok/templates/agents-index.md) |
| Agent 지침 변경 제안 채팅 양식 | [aok/templates/agent-change-proposal.md](aok/templates/agent-change-proposal.md) |
| 하위 `AGENTS.md` | [aok/templates/subdir-agents.md](aok/templates/subdir-agents.md) |
| ADR | [aok/templates/adr.md](aok/templates/adr.md) |
| 현재 상태 문서 | [aok/templates/current-status.md](aok/templates/current-status.md) |
| 버전 이력 | [aok/templates/version-history.md](aok/templates/version-history.md) |
| 작업 로그 | [aok/templates/work-log.md](aok/templates/work-log.md) |

## Workflow 템플릿

| 작업 유형 | 파일 |
|---|---|
| 기능 추가 / 동작 변경 | [aok/workflows/feature-change.md](aok/workflows/feature-change.md) |
| 버그 수정 | [aok/workflows/bugfix.md](aok/workflows/bugfix.md) |
| 리팩터링 | [aok/workflows/refactor.md](aok/workflows/refactor.md) |
| 문서 / 정책 / ADR 변경 | [aok/workflows/docs-change.md](aok/workflows/docs-change.md) |
| 설정 / 빌드 / CI / 의존성 / 배포 / DB 변경 | [aok/workflows/risky-change.md](aok/workflows/risky-change.md) |
| 조사 / 의사결정 / 기술 선택 | [aok/workflows/research-decision.md](aok/workflows/research-decision.md) |
| 리뷰 피드백 반영 | [aok/workflows/review-feedback.md](aok/workflows/review-feedback.md) |
| 반복 실패 / 프로젝트 전용 스킬화 | [aok/workflows/repeated-failure.md](aok/workflows/repeated-failure.md) |

## 적용 메모

- 기존 프로젝트에 적용할 때는 먼저 기존 문서와 workflow를 읽고, 원본 보존 방식과 충돌 처리 방식을 사용자에게 선택지로 묻는다.
- 새 문서나 지침 파일을 실제 프로젝트에 만들기 전에는 생성, 수정, 이동, archive 대상 파일 목록을 제안하고 사용자 승인을 받는다.
- 필요한 작업에 해당하는 문서만 읽는다. 전체 AOK를 기본으로 모두 읽지 않는다.
- 적용 결과물에는 `[명령어]`, `[경로]`, TODO 같은 미해결 placeholder를 남기지 않는다. 알 수 없는 값은 본문에 넣지 말고 확인 필요 항목으로 분리한다.
