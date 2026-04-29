# 리팩터링 Workflow

> 관리 대상 agent workflow 문서입니다. 사용자 승인 없이 의미를 바꾸는 수정은 하지 않습니다.
> 전제: 이 workflow는 Superpowers 스킬이 설치된 agent 환경을 기준으로 한다.

## 목적

외부 동작을 보존하면서 구조를 개선한다. 리팩터링 중 기능 변경이 섞이지 않게 한다.

## 절차

1. 중간 이상 리팩터링은 `brainstorming`으로 범위, 목표, 금지할 동작 변경을 정리한다.
2. 범위가 넓으면 `writing-plans`로 단계별 계획을 작성한다.
3. 기존 동작 보존 테스트를 먼저 작성한다. 동작 보존이 핵심이면 `test-driven-development`를 사용한다.
4. 계획이 있으면 `executing-plans`로 작게 나누어 실행한다.
5. 독립 영역이 명확하고 사용자가 허용한 경우에만 `subagent-driven-development` 또는 `dispatching-parallel-agents`를 사용한다.
6. 중간 이상 리팩터링, 공유 경계 변경, 회귀 위험이 있는 경우 `requesting-code-review`로 외부 동작 변경, 책임 경계, 테스트 누락을 확인한다.
7. 리뷰 피드백은 `receiving-code-review`로 검토한 뒤 반영한다.
8. `verification-before-completion`으로 기존 동작 보존이 검증됐는지 확인한다.

## 완료 전 확인

- 리팩터링 범위와 금지할 동작 변경을 명시했는가?
- 기존 동작 보존 테스트나 대체 검증이 있는가?
- 기능 변경이 섞였다면 별도 동작 변경으로 다루었는가?
- 완료 전 실제 검증 결과를 확인했는가?
