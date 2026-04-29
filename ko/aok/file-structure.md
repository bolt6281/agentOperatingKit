# 권장 파일 구조

이 문서는 AOK가 사용하는 경로와 파일 역할의 기준 카탈로그다. 채택 레벨, 적용 가이드, 템플릿 문서는 필요한 범위를 설명하되, 기본 경로와 구조가 충돌하면 이 문서를 우선한다.

```text
~/.codex/AGENTS.md (선택)
  모든 프로젝트에 적용되는 개인 전역 원칙
  사용자가 명시적으로 선택한 경우에만 제안하거나 수정한다.

<repo>/AGENTS.md
  해당 프로젝트의 구조, 공통 명령어, 검증 라우팅, 문서 지도, 지침 파일 거버넌스

<repo>/.agents/INDEX.md
  workflow 색인과 승인된 agent 지침 파일 목록

<repo>/.agents/workflows/*.md
  기능 추가, 버그 수정, 리팩터링 같은 작업별 절차 문서
  Superpowers를 사용하는 프로젝트에서만 생성한다.

<repo>/.agents/skills/
  반복 실패나 프로젝트 고유 판단 절차가 안정된 경우에만 두는 프로젝트 전용 skill
  생성하거나 의미를 바꾸는 수정은 사용자 승인 후에만 한다.

<repo>/.agents/skills/INDEX.md (선택)
  프로젝트 전용 skill이 많아졌을 때만 만드는 skill 전용 색인
  기본적으로는 .agents/INDEX.md의 프로젝트 전용 skill 표를 사용한다.

<repo>/<영역>/AGENTS.md
  특정 영역에만 적용되는 코드 작성 규칙, 디자인 톤, 검증 방식
  생성하거나 의미를 바꾸는 수정은 사용자 승인 후에만 한다.

<repo>/docs/
  기준 문서, 운영 메모, 빌드 가이드

<repo>/docs/README.md 또는 <repo>/docs/INDEX.md
  문서가 많아졌을 때만 만드는 프로젝트 문서 색인
  현재 기준 문서와 반복 참조 문서만 올린다.

<repo>/docs/archive/
  폐기된 문서, 백업 문서, 원본 참고 자료
  현재 기준 문서로 사용하지 않는다.

<repo>/docs/superpowers/
  Superpowers skill 운용 결과물을 보관하는 폴더
  예: specs, plans, review notes, skill 작업 결과

<repo>/docs/adr.md
  작은 프로젝트에서 사용하는 단일 ADR 기준 문서

<repo>/docs/adr/INDEX.md
  ADR이 커졌을 때 사용하는 ADR 라우터
  영역, ADR 경로, 상태, 읽는 조건을 표로 관리한다.

<repo>/docs/adr/<영역>/<결정-주제>.md
  ADR이 커졌을 때 사용하는 영역별 결정 문서
  예: product/notification-policy.md, architecture/app-web-boundary.md, data/job-status-model.md, operations/deployment-policy.md, ux/worker-flow.md
  단순 순번식 파일명보다 영역과 주제를 드러내는 파일명을 우선한다.

<repo>/docs/current-status.md (선택)
  현재 운영 상태, 검증 기준, 배포/외부 의존성, 남은 위험을 짧게 기록하는 문서
  작업 로그나 과거 변경 이력을 누적하지 않는다.

<repo>/docs/VERSION_HISTORY.md
  주요 버전별 변경 내역과 의사결정 이력

<repo>/docs/work-log.md (선택)
  과거 구현 흐름, 복구/롤백 참고, 장기 운영 메모
  평소 작업 시작 시 읽지 않고 기록 대상으로만 사용한다.
  롤백, 복구, 장애 조사, 회귀 원인 추적처럼 과거 흐름이 필요할 때만 읽는다.
```
