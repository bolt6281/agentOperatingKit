# 설정 / 빌드 / CI / 의존성 / 배포 / DB 변경 Workflow

> 관리 대상 agent workflow 문서입니다. 사용자 승인 없이 의미를 바꾸는 수정은 하지 않습니다.
> 전제: 이 workflow는 Superpowers 스킬이 설치된 agent 환경을 기준으로 한다.

## 목적

운영 영향이 큰 변경을 작은 단위로 적용하고, 영향 범위와 롤백 가능성을 먼저 확인한다.

## 적용 대상

- 설정 파일 변경
- 빌드 또는 CI 변경
- 의존성 추가, 제거, 업그레이드
- 배포 설정 변경
- DB 스키마, migration, seed, 데이터 처리 변경
- 인증, 권한, 결제, 보안 관련 변경

## 고위험 승인 카드

배포, migration, secret, production data, 인증/권한, 결제, 보안, 개인정보 또는 민감 데이터에 영향을 줄 수 있으면 파일을 수정하기 전에 아래 항목을 사용자에게 제시하고 명시 승인을 받는다.

| 항목 | 확인 내용 |
|---|---|
| 변경 유형 | 설정 / 빌드 / CI / 의존성 / 배포 / DB / 인증 / 권한 / 결제 / 보안 / 데이터 처리 중 해당 항목 |
| 영향 데이터 | production data, 개인정보, 민감 정보, 결제 정보, 감사 대상 데이터 영향 여부 |
| PII/PHI 여부 | 개인정보 또는 건강정보 같은 규제 대상 데이터 포함 여부 |
| migration 방향 | forward-only, reversible, data backfill, destructive change 여부 |
| 백업/복구 | 백업 필요 여부, 복구 지점, 복구 확인 방법 |
| 롤백 가능성 | 코드 롤백만으로 충분한지, DB/data rollback이 필요한지 |
| 승인자/감사 티켓 | 승인자, issue/PR/ticket/deploy log 위치 |
| 배포 창 | 즉시 적용 가능 여부, maintenance window, 사용자 영향 시간 |
| dry-run | migration dry-run, staging 검증, 샘플 데이터 검증 가능 여부 |
| 모니터링 기준 | 배포 후 확인할 metric, log, alert, error budget 기준 |

## 절차

1. 관련 문서와 현재 설정 파일을 먼저 확인한다.
2. 영향 범위, 롤백 방법, 로컬 검증 방법을 정리한다.
3. 배포, migration, secret, production data, 인증/권한, 결제, 보안, 개인정보, 민감 데이터에 영향을 줄 수 있으면 변경 전 고위험 승인 카드를 제시하고 명시 승인을 받는다.
4. 위험도가 높거나 여러 파일을 건드리면 `using-git-worktrees`를 사용한다.
5. 동작 변경이나 마이그레이션이 있으면 가능한 범위에서 `test-driven-development`를 사용한다.
6. 변경은 최소 단위로 적용하고, 설정/빌드/마이그레이션 검증 명령을 실행한다.
7. 운영 리스크가 있거나 검증 범위가 넓은 경우 `requesting-code-review`로 누락된 검증을 확인한다.
8. `verification-before-completion`으로 실제 검증 결과를 확인한다.

## 완료 전 확인

- 관련 문서와 현재 설정 파일을 먼저 확인했는가?
- 영향 범위, 롤백 방법, 로컬 검증 방법을 정리했는가?
- 배포, migration, secret, production data, 인증/권한, 결제, 보안, 개인정보, 민감 데이터 영향 변경은 고위험 승인 카드로 사용자 승인을 받은 뒤 진행했는가?
- 실제 검증 명령을 실행했는가?
