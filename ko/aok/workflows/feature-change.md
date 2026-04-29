# 기능 추가 / 동작 변경 Workflow

> 관리 대상 agent workflow 문서입니다. 사용자 승인 없이 의미를 바꾸는 수정은 하지 않습니다.
> 전제: 이 workflow는 Superpowers 스킬이 설치된 agent 환경을 기준으로 한다.

## 목적

새 기능을 추가하거나 기존 동작을 바꿀 때, 작업 규모를 먼저 판정하고 그에 맞는 절차로 진행한다.

## 절차

1. 먼저 작업 규모를 판정한다.
   - 축약형: 단일 파일 또는 좁은 범위, 요구사항이 명확함, public API/DB/배포/빌드/권한/보안 영향 없음, 회귀 위험 낮음.
   - 표준형: 여러 파일, 새 동작 설계, 사용자 흐름 변경, 상태/데이터/API 변경, 테스트 전략이 필요한 작업.
   - 고위험형: DB, 인증/권한, 결제, 배포, 마이그레이션, 빌드/CI, 데이터 손실 가능성이 있는 작업.
2. 고위험형이면 이 workflow를 계속 진행하지 않는다. `.agents/workflows/risky-change.md`를 먼저 읽고 그 workflow로 전환한다.
   - 기능 요구사항은 `risky-change.md`의 영향 범위, 롤백, 검증 계획 안에 포함한다.
   - 고위험 작업을 기능 추가로도 볼 수 있더라도 workflow 우선순위는 `risky-change.md`가 앞선다.
3. 축약형은 `brainstorming`의 원칙을 축약 적용해 목적, 변경 범위, 검증 방법을 짧게 확인하고 inline execution으로 진행한다.
   - `writing-plans` 문서화와 `executing-plans`는 생략할 수 있다.
   - 동작 변경이면 가능한 최소 테스트 또는 재현 확인을 추가한다.
   - 완료 전 `verification-before-completion`으로 실제 검증 결과를 확인한다.
4. 표준형은 `brainstorming`으로 목적, 사용자, 성공 기준, 범위, 비범위를 정리한다.
5. 필요한 경우 `clarify`로 모호한 요구사항을 선택지 중심으로 좁힌다.
6. 사용자 승인 후 `writing-plans`로 구현 계획을 작성한다.
7. 계획이 준비되면 `executing-plans`로 단계별 실행한다.
8. 검증 가능한 동작 변경은 `test-driven-development`를 사용해 실패 테스트를 먼저 만든다.
9. 독립 작업 분리가 적절하고 사용자가 허용한 경우에만 `dispatching-parallel-agents` 또는 `subagent-driven-development`를 사용한다.
10. 중간 이상 변경, 공유 경계 변경, 회귀 위험이 있는 경우 주요 체크포인트마다 `requesting-code-review`를 사용한다.
11. 리뷰 피드백을 받으면 `receiving-code-review`로 타당성을 확인한 뒤 반영한다.
12. `verification-before-completion`으로 테스트, 빌드, 수동 검증 등 실제 결과를 확인한다.
13. 브랜치 단위 작업이면 `finishing-a-development-branch`로 마무리한다.

## 완료 전 확인

- 작업 규모 판정이 맞는가?
- 고위험형이면 `risky-change.md`로 전환했는가?
- 필요한 Superpowers 스킬을 적용했는가?
- 동작 변경에 대한 테스트나 재현 확인이 있는가?
- 완료 선언 전에 실제 검증 결과를 확인했는가?
