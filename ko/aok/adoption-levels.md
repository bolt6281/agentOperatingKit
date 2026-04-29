# 채택 레벨

이 템플릿은 처음부터 전체 구조를 만들기 위한 문서가 아니다. AOK 적용 인터뷰의 선택 결과에 따라 필요한 범위만 단계적으로 채택한다.

## Level 1. 최소 적용

적용 대상:
- 신규 개발을 시작하지만 아직 작업 절차가 복잡하지 않은 repo
- 개인 프로젝트, 작은 라이브러리, 단기 실험
- agent 작업 빈도가 낮고 문서 거버넌스가 아직 필요하지 않은 repo

생성 파일:
- `<repo>/AGENTS.md`

원칙:
- 프로젝트 개요, 공통 명령어, 검증 방법만 적는다.
- `.agents/`, `docs/adr.md`, `docs/VERSION_HISTORY.md`, `docs/work-log.md`는 만들지 않는다.
- workflow 문서는 같은 절차가 반복될 때만 승격한다.

## Level 2. Workflow 적용

적용 대상:
- LLM과 반복적으로 작업하는 프로젝트
- 기능 추가, 버그 수정, 리팩터링이 계속 발생하는 repo
- 작업 파이프라인 정립과 컨텍스트 절감이 필요한 프로젝트
- Superpowers 스킬을 설치했거나 설치할 프로젝트

생성 파일:
- `<repo>/AGENTS.md`
- `<repo>/.agents/INDEX.md`
- 필요한 `.agents/workflows/*.md` 일부

원칙:
- 루트 `AGENTS.md`는 라우터 역할만 한다.
- 긴 절차는 Superpowers 사용 환경에서만 workflow 문서로 분리한다.
- 실제로 쓰는 workflow만 만든다.
- 일반 프로젝트 문서는 루트 `AGENTS.md`의 문서 지도만으로 관리하고, 별도 `docs/INDEX.md`는 만들지 않는다.
- Superpowers를 쓰지 않는 프로젝트는 Level 2 workflow 구조를 적용하지 않는다.

## Level 3. 문서 거버넌스 적용

적용 대상:
- 장기 운영 프로젝트
- 여러 agent 또는 여러 사람이 함께 작업하는 repo
- 문서 정합성 회복, source of truth 관리, 의사결정 이력이 중요한 프로젝트
- 배포, 마이그레이션, 정책 변경, 위험 작업 통제가 필요한 프로젝트

생성 파일:
- Level 2 전체
- 선택한 Level 3 문서 거버넌스 파일
- 필요한 하위 `AGENTS.md`

기본 경로와 파일 역할은 [권장 파일 구조](file-structure.md)를 따른다. 이 문서는 어떤 상황에서 Level 3 문서를 만들지 결정하는 기준만 둔다.

원칙:
- 하위 `AGENTS.md`는 반복 규칙과 명확한 적용 범위가 있을 때만 만든다.
- 각 지침 파일에는 소유자, 적용 범위, 마지막 검토일을 둔다.
- 문서 추가보다 기존 문서 갱신을 우선한다.
- 문서 색인은 현재 기준 문서와 반복 참조 문서만 대상으로 한다.
- `docs/current-status.md`는 현재 운영 상태, 검증 기준, 배포/외부 의존성, 남은 위험을 짧게 유지해야 할 때만 만든다.
- `docs/work-log.md`는 issue, PR, plan으로 추적하기 어려운 장기 운영 메모가 있을 때만 만들고, 평소에는 읽지 않는다. 롤백, 복구, 장애 조사, 회귀 원인 추적처럼 과거 흐름이 필요한 경우에만 읽는다.
- 단일 `docs/adr.md`가 커지면 `docs/adr/` 디렉터리 구조로 승격한다.
- ADR 파일명은 단순 번호보다 도메인과 주제를 우선한다. 예: `docs/adr/product/notification-policy.md`, `docs/adr/architecture/app-web-boundary.md`, `docs/adr/operations/deployment-policy.md`
- `docs/adr/INDEX.md`는 시간순 목록이 아니라 변경 영역별 라우터로 작성한다.

## 대표 적용 예시

| 프로젝트 상황 | 기본 추천 | 만들지 않는 파일 | 이유 |
|---|---|---|---|
| 작은 신규 CLI 또는 개인 실험 repo | Level 1: 루트 `AGENTS.md`만 | `.agents/`, ADR, VERSION_HISTORY, work-log | 작업 절차와 문서 거버넌스가 아직 반복되지 않는다. 확인되지 않은 테스트/빌드 명령은 `확인 필요 항목`으로 남긴다. |
| Superpowers를 쓰지 않는 기존 소규모 앱에서 README, plan, architecture가 충돌함 | Custom: Level 1 + 필요한 경우 짧은 `docs/current-status.md` | `.agents/workflows/`, ADR, VERSION_HISTORY, work-log | 문서 정합성 회복이 목적이어도 workflow와 전체 Level 3 구조를 자동 생성하지 않는다. 기존 문서는 보존하고 충돌 후보로 표시한다. |
| 공개 오픈소스 라이브러리에서 README, CONTRIBUTING, CHANGELOG 또는 release note가 이미 있음 | Custom: Level 1 + 기존 contributor-facing 문서 보강 | `.agents/workflows/`, `docs/VERSION_HISTORY.md`, ADR, current-status, work-log | 외부 기여자 문서 부담을 늘리지 않는다. 릴리스 기준은 새 파일보다 기존 CHANGELOG, release note, CONTRIBUTING 보강을 우선한다. |

## Custom 적용

사용자가 특정 AOK 구성 요소만 선택한 경우에는 Level 1~3 중 하나로 억지로 맞추지 않고 Custom 적용안으로 제안한다.

Custom 적용에서도 다음 원칙은 유지한다.

- 생성, 수정, 이동, archive 대상 파일을 먼저 제안한다.
- 기존 문서의 의미를 바꾸는 변경은 사용자 승인 후 진행한다.
- 선택하지 않은 AOK 구성 요소는 만들지 않는다.

## 혼합 채택

기존 프로젝트는 Level 2와 Level 3가 깔끔하게 나뉘지 않을 수 있다. 예를 들어 workflow는 아직 없지만 `docs/adr.md`, `docs/current-status.md`, `docs/VERSION_HISTORY.md`, `docs/work-log.md`, `docs/archive/` 같은 Level 3 성격 문서가 이미 있을 수 있다.

이 경우에는 억지로 전체 Level 3를 적용하지 않고, 적용안을 `Level 2 + 기존 문서 거버넌스 보존` 또는 `Custom`으로 표시한다.

원칙:

- 이미 있는 Level 3 성격 문서는 삭제하거나 이동하지 않는다.
- 새 Level 3 문서를 자동으로 추가하지 않는다.
- 기존 문서는 루트 `AGENTS.md`의 문서 지도에 상태와 기준 여부를 기록한다.
- workflow는 Superpowers 사용 여부와 반복 작업 필요성에 따라 별도로 판단한다.
- 큰 `AGENTS.md`가 이미 있으면 루트 라우터, `.agents/INDEX.md`, workflow, 일반 docs로 분해할 후보를 먼저 제안한다.
- 기존 문서가 오래됐거나 충돌하면 source of truth를 즉시 확정하지 말고 충돌 후보로 남긴다.

## 승격 기준

다음 조건 중 하나가 반복되면 다음 레벨로 승격을 검토한다.

- 같은 작업 절차를 매번 설명하고 있다.
- agent가 같은 유형의 실수를 반복한다.
- 문서 위치를 찾는 데 시간이 든다.
- 검증 명령이나 작업 경계가 자주 혼동된다.
- 의사결정 이력이 코드와 어긋나기 시작한다.

처음부터 Level 3 구조를 만들지 않는다. 필요한 순간에 필요한 파일만 추가하고, 추가할 파일의 기본 경로는 [권장 파일 구조](file-structure.md)를 기준으로 확인한다.
