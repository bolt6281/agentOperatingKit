# Agent 작업 절차 색인

작업이 해당될 때만 필요한 문서를 읽는다. 모든 workflow 문서를 기본으로 읽지 않는다.
이 문서는 agent 지침 파일, workflow, 프로젝트 전용 skill만 색인한다. 제품, 운영, ADR, 릴리스, 작업 로그 같은 일반 프로젝트 문서는 루트 `AGENTS.md`의 문서 라우팅이나 선택 문서 지도 섹션에서 관리한다.

## 공통 라우팅

- 사용자 지시가 불명확하거나 요구사항 충돌, 위험한 가정이 보이면 먼저 정리한다.
- 이미 승인된 구현 계획이 있으면 새로 설계하지 않고 그 계획을 실행한다.
- 작업 규모가 중간 이상이거나 위험도가 높으면 별도 작업 공간, 롤백 방법, 영향 범위를 먼저 고려한다.
- 독립 작업이 2개 이상이어도 사용자가 병렬/서브에이전트 작업을 명시적으로 허용한 경우에만 병렬화한다.
- 완료 선언 전에는 실제 검증 결과를 확인한다.
- Superpowers를 쓰지 않는 프로젝트에서는 `.agents/workflows/*.md`를 사용하지 않는다.

## Workflow 우선순위 라우팅

Superpowers workflow를 적용한 프로젝트에서만 이 표를 사용한다. 여러 조건에 동시에 해당하면 위에 있는 항목을 먼저 따른다.

| 우선순위 | 조건 | 먼저 읽을 workflow |
|---|---|---|
| 1 | DB, migration, 인증/권한, 결제, 보안, 배포, CI, 의존성, 빌드 설정 변경 | `.agents/workflows/risky-change.md` |
| 2 | 버그 재현, 회귀, 장애, 예외 동작 수정 | `.agents/workflows/bugfix.md` |
| 3 | 리뷰 피드백 반영 | `.agents/workflows/review-feedback.md` |
| 4 | 문서, 정책, ADR, agent 지침 변경 | `.agents/workflows/docs-change.md` |
| 5 | 외부 동작 보존을 전제로 한 구조 개선 | `.agents/workflows/refactor.md` |
| 6 | 조사, 비교, 기술 선택, 의사결정 | `.agents/workflows/research-decision.md` |
| 7 | 기능 추가 또는 일반 동작 변경 | `.agents/workflows/feature-change.md` |
| 8 | 같은 실패가 반복되어 문서, skill, 자동화 중 어떤 방식으로 막을지 판단 | `.agents/workflows/repeated-failure.md` |

## INDEX 유지 규칙

`.agents/INDEX.md`는 agent 문서의 현재 지도를 나타낸다. 실제 파일 구조와 다르면 INDEX를 신뢰하지 않는다.

## 템플릿 적용 규칙

이 파일을 실제 프로젝트의 `.agents/INDEX.md`로 적용할 때는 예시 placeholder를 그대로 남기지 않는다.

- `[YYYY-MM-DD]`, `[작업 유형]`, `[파일명]`, `[skill-name]`, `[언제 사용하는지]`는 실제 값으로 바꾼다.
- 실제 값이 없으면 예시 행을 삭제하거나 `없음` 행으로 바꾼다.
- 사용자 승인을 받지 않은 workflow나 skill은 `Workflow 문서` 또는 `프로젝트 전용 skill` 표에 올리지 않는다.
- AOK가 제공하는 후보는 `선택 가능한 workflow 후보` 표에만 둔다.

### 갱신해야 하는 경우

다음 변경이 발생하면 같은 작업 안에서 INDEX도 갱신한다.

- `AGENTS.md` 또는 하위 `AGENTS.md`를 새로 만들 때
- agent 지침 파일을 삭제하거나 이동할 때
- workflow 문서를 추가, 삭제, 이름 변경할 때
- 프로젝트 전용 skill을 추가, 삭제, 이름 변경할 때
- 지침 파일의 적용 범위가 바뀔 때
- 문서의 소유자 또는 마지막 검토일이 바뀔 때
- workflow가 더 이상 사용되지 않아 deprecated 처리할 때

### 색인 항목 상태

각 agent 지침 파일과 workflow 문서는 다음 상태 중 하나를 가진다.

- `active`: 현재 사용하는 공식 문서
- `draft`: 제안 또는 실험 중인 문서
- `deprecated`: 더 이상 새 작업에 쓰지 않는 문서
- `archived`: 보존 목적 문서

`deprecated` 또는 `archived` 문서는 새 작업의 기본 기준으로 사용하지 않는다.

### 부패 징후

다음 징후가 보이면 INDEX를 먼저 점검한다.

- INDEX에 있는 파일이 실제로 존재하지 않는다.
- 실제 workflow 파일이 있는데 INDEX에 없다.
- 문서의 적용 범위와 실제 repo 구조가 다르다.
- 마지막 검토일이 오래되었고 최근 구조 변경이 있었다.
- agent가 INDEX와 다른 문서를 기준으로 작업하고 있다.

## 승인된 지침 파일

이 문서에 없는 agent 지침 파일은 새로 만들기 전에 사용자 승인을 받아야 한다.

| 경로 | 상태 | 적용 범위 | 목적 | 소유자 | 마지막 검토 | 비고 |
|---|---|---|---|---|---|---|
| `AGENTS.md` | active | 전체 repo | 프로젝트 기본 지침 | Maintainers | `[YYYY-MM-DD]` |  |

## Workflow 문서

이 표에는 실제로 생성했거나 사용자 승인을 받은 workflow만 적는다.

| 작업 유형 | 상태 | 문서 |
|---|---|---|
| `[작업 유형]` | active | `.agents/workflows/[파일명].md` |

승인된 workflow가 없으면 위 예시 행을 삭제하고 아래처럼 적는다.

| 작업 유형 | 상태 | 문서 |
|---|---|---|
| 없음 | - | - |

## 선택 가능한 workflow 후보

아래 항목은 AOK가 제공하는 후보 목록이다. 적용한 항목만 위 `Workflow 문서` 표에 올린다.
후보 표는 그대로 전부 복사하는 목록이 아니다. 반복 빈도, 실패 비용, Superpowers 사용 여부, 함께 생성해야 할 workflow를 확인한 뒤 실제로 쓸 항목만 선택한다.

| 작업 유형 | 후보 문서 | 반복 빈도 기준 | 실패 비용 | Superpowers 필요 | 함께 생성 권장 |
|---|---|---|---|---|---|
| 기능 추가 / 동작 변경 | `.agents/workflows/feature-change.md` | 기능 또는 동작 변경이 반복되고 요구사항/검증 범위 정리가 필요함 | 중간 | 필수 | 고위험 기능이 자주 있으면 `risky-change.md` |
| 버그 수정 | `.agents/workflows/bugfix.md` | 재현, 회귀 확인, 원인 분석 절차가 반복됨 | 중간 | 필수 | 장애/운영 회귀가 잦으면 `risky-change.md` |
| 리팩터링 | `.agents/workflows/refactor.md` | 외부 동작 보존과 구조 개선을 분리하는 일이 반복됨 | 중간 | 필수 | 대규모 공유 경계 변경이면 `review-feedback.md` |
| 문서 / 정책 / ADR 변경 | `.agents/workflows/docs-change.md` | 문서 의미 변경, source of truth, ADR, agent 지침 변경이 반복됨 | 낮음~중간 | 필수 | 첫 AOK 적용은 `application-guide.md`를 우선하고 이 workflow로 처리하지 않음 |
| 설정 / 빌드 / CI / 의존성 / 배포 / DB 변경 | `.agents/workflows/risky-change.md` | DB, 배포, CI, secret, 인증/권한, 결제, 보안 변경이 반복되거나 실패 비용이 큼 | 높음 | 필수 | 고위험 기능, 운영 버그, migration 작업과 함께 우선 생성 |
| 조사 / 의사결정 / 기술 선택 | `.agents/workflows/research-decision.md` | 비교 조사와 의사결정 근거 작성이 반복됨 | 중간~높음 | 필수 | 결정 뒤 구현이 이어지면 `feature-change.md` 또는 `risky-change.md` |
| 리뷰 피드백 반영 | `.agents/workflows/review-feedback.md` | 리뷰 반영 전 타당성 확인과 범위 조정이 반복됨 | 중간 | 필수 | 기능/리팩터링 workflow와 함께 사용 가능 |
| 반복 실패 / 프로젝트 전용 스킬화 | `.agents/workflows/repeated-failure.md` | 같은 실패가 반복되고 테스트/린트/CI만으로 막기 어려움 | 중간~높음 | 필수 | 안정된 판단 절차가 생긴 뒤 프로젝트 전용 skill 후보 |

## 프로젝트 전용 skill

이 표에는 실제로 생성했거나 사용자 승인을 받은 프로젝트 전용 skill만 적는다.

| skill | 상태 | 문서 | 사용 조건 |
|---|---|---|---|
| `[skill-name]` | active | `.agents/skills/[skill-name]/SKILL.md` | `[언제 사용하는지]` |

승인된 프로젝트 전용 skill이 없으면 위 예시 행을 삭제하고 아래처럼 적는다.

| skill | 상태 | 문서 | 사용 조건 |
|---|---|---|---|
| 없음 | - | - | - |

프로젝트 전용 skill이 많아져 이 표만으로 관리하기 어렵다면 사용자 승인 후 `.agents/skills/INDEX.md`를 별도로 만든다. 기본 구조에서는 별도 skill INDEX를 만들지 않는다.
