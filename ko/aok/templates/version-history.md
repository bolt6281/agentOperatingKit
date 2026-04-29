# Version history 템플릿

이 템플릿은 주요 버전, 릴리스 기준, 배포 산출물, 사용자 노출 변경을 한 곳에서 추적할 때 사용한다.

`docs/VERSION_HISTORY.md`는 일반 작업 로그가 아니다. 버전 기준이 바뀌지 않은 상세 구현 이력은 `docs/work-log.md`에 남기고, 결정 근거는 ADR에 둔다.

이미 `CHANGELOG`, release note, GitHub Releases, `CONTRIBUTING`의 릴리스 기준 섹션처럼 같은 역할을 하는 문서가 있으면 새 `docs/VERSION_HISTORY.md`를 만들지 않는다. 먼저 기존 문서를 보강하고, 기존 문서만으로 버전 기준과 배포 산출물을 안정적으로 추적하기 어려울 때만 이 템플릿을 적용한다.

# Version History

현재 스테이징 빌드: `[버전 또는 해당 없음]`

현재 릴리스 기준: `[버전 또는 해당 없음]`

이 문서는 릴리스 간 변경, 릴리스 기준, 배포 산출물을 추적한다.
버전, 릴리스 기준, 배포 산출물이 바뀔 때만 version/build 파일과 함께 갱신한다.

## 운영 규칙

- 사용자 또는 릴리스 절차가 명시적으로 요구할 때만 버전을 올린다.
- 기능 변경이 반영됐다는 이유만으로 버전을 올리지 않는다.
- 기존 CHANGELOG 또는 release note와 중복되면 이 파일을 만들지 말고 기존 문서를 source of truth로 유지한다.
- 사용자 노출 버전, 플랫폼 빌드 번호, 배포 산출물 이름을 맞춘다.
- 릴리스 패키지를 만들면 산출물 유형과 경로를 기록한다.

## 비교 요약

| 버전 | 기준 상태 | 변경 요약 |
|---|---|---|
| `[version]` | current staged build / current release baseline / previous release baseline | `[one-line summary]` |

## `[version]`

이전 버전: `[previous version or none]`

### 변경

- `[release-to-release change]`
- `[build, deployment, data, or compatibility change]`

### 릴리스 노트

- 사용자 노출 버전: `[version]`
- 플랫폼 빌드 번호: `[versionCode, build number, or 해당 없음]`
- 릴리스 산출물: `[artifact path or deployment URL]`
- `[user-facing release note]`

## 적용 시 주의

- 최신 버전을 위에 둔다.
- 기존 CHANGELOG, release note, GitHub Releases가 있으면 새 문서를 만들기 전에 그 문서 보강으로 충분한지 먼저 확인한다.
- 스테이징 빌드 개념이 없는 프로젝트는 `현재 릴리스 기준`만 사용한다.
- 모바일/빌드 산출물이 없는 프로젝트는 플랫폼 빌드 번호 행을 억지로 채우지 말고 삭제한다.
- 실제 프로젝트에 적용할 때는 placeholder를 남기지 않는다.
