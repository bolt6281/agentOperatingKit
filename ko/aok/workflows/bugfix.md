# 버그 수정 Workflow

> 관리 대상 agent workflow 문서입니다. 사용자 승인 없이 의미를 바꾸는 수정은 하지 않습니다.
> 전제: 이 workflow는 Superpowers 스킬이 설치된 agent 환경을 기준으로 한다.

## 목적

버그를 추측으로 고치지 않고, 재현 조건과 root cause를 확인한 뒤 최소 수정으로 해결한다.

## 절차

1. `systematic-debugging`을 사용한다.
2. 재현 조건, 기대 동작, 실제 동작, 영향 범위를 확인한다.
3. root cause를 확인하고, 가능한 원인 후보를 배제한 근거를 남긴다.
4. `test-driven-development`로 실패 테스트나 재현 스크립트를 먼저 만든다.
5. 최소 수정으로 구현한다.
6. 중간 이상 수정, 공유 경계 변경, 회귀 위험이 있는 경우 `requesting-code-review`로 수정 방향과 회귀 위험을 확인한다.
7. 리뷰 피드백을 받으면 `receiving-code-review`로 검토한다.
8. `verification-before-completion`으로 재현 케이스와 관련 회귀 테스트가 통과했는지 확인한다.

## 완료 전 확인

- 재현 조건과 기대/실제 동작을 분리해 확인했는가?
- root cause를 확인했는가?
- 실패 테스트나 재현 스크립트를 먼저 만들었는가, 또는 만들 수 없는 이유를 설명했는가?
- 관련 회귀 검증을 실제로 실행했는가?
