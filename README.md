# Agent Operating Kit

Agent Operating Kit(AOK) is a documentation and workflow template pack for operating software projects with coding agents.

AOK is not a bigger prompt. It is a template pack for keeping always-read agent instructions small, while moving optional workflows and project knowledge into discoverable documents that agents read only when relevant.

Korean version: [한국어](#한국어)

## Why AOK Exists

Projects that use coding agents for real work often run into the same operational problems:

- A repo has planning documents, but no clear path for starting implementation.
- Feature work, bug fixes, refactors, and documentation changes follow inconsistent processes.
- Agent-written documents drift away from code and from each other.
- `AGENTS.md` or planning documents grow too large, wasting context even for small tasks.
- Existing projects need agent operating rules, but blindly replacing old documents risks losing important details.

AOK addresses these problems by splitting agent instructions, workflows, document maps, and governance rules into small files that can be adopted selectively.

## Core Principles

- Keep the root `AGENTS.md` short enough to read every session. Prefer 50-100 lines for small projects.
- Select only the components the project actually needs.
- Ask the user which parts of AOK they want before applying it.
- Read existing project documents before restructuring them.
- Preserve details and avoid information loss when migrating old documents.
- Ask for approval before moving, deleting, deprecating, or archiving existing files.
- Create `.agents/workflows/*.md` only for projects that use Superpowers.
- If Superpowers is not used, do not provide AOK workflow documents; apply only the basic root `AGENTS.md` operating guidance.
- Treat global instruction files such as `~/.codex/AGENTS.md` as optional.

AOK succeeds when it reduces the amount of context an agent must read for ordinary work. If applying AOK makes every task read more documents by default, the application is wrong.

## Quick Start

Ask your agent:

```text
I want to apply Agent Operating Kit to this repo.
Read en/agentOperatingKit.md first and follow the AOK application guide.
Do not modify existing files immediately. Propose an application plan first.
```

The agent should start with [en/agentOperatingKit.md](en/agentOperatingKit.md), then read only the documents needed for the selected scope:

1. [AOK Application Guide](en/aok/application-guide.md)
2. [Component Selection Guide](en/aok/component-selection.md)
3. [Recommended File Structure](en/aok/file-structure.md)
4. [Superpowers Installation and Workflow Preconditions](en/aok/superpowers-install.md), if workflows are selected
5. The selected template or workflow files

## Component Selection

AOK is not installed through a fixed sequence. It is a template pack where each project selects only the components it needs.

| Component | Use When |
|---|---|
| Root `AGENTS.md` | The agent needs always-read project overview, commands, and verification routing |
| `DESIGN.md` | UI/frontend work needs a routed visual baseline for colors, typography, spacing, and components |
| Document map / instruction governance sections | Document source-of-truth status or agent instruction change approval rules are needed |
| `.agents/INDEX.md` | Workflows, nested agent instructions, or project-specific skills need an index |
| `.agents/workflows/*.md` | The project uses Superpowers and the same work procedure repeats |
| ADR / current status / version history | Long-running operation, document consistency, or decision history needs governance |
| `docs/work-log.md` | Rollback, recovery, incident investigation, or regression tracing needs historical context |

See [en/aok/component-selection.md](en/aok/component-selection.md) for details.

## Repository Structure

```text
README.md
ko/
  aok/
  agentOperatingKit.md
en/
  aok/
  agentOperatingKit.md
```

## Main Documents

| Document | Purpose |
|---|---|
| [en/agentOperatingKit.md](en/agentOperatingKit.md) | Main English AOK index |
| [en/aok/application-guide.md](en/aok/application-guide.md) | User interview and existing-project adoption rules |
| [en/aok/component-selection.md](en/aok/component-selection.md) | AOK component selection criteria |
| [en/aok/file-structure.md](en/aok/file-structure.md) | Recommended AOK file structure |
| [en/aok/superpowers-install.md](en/aok/superpowers-install.md) | Superpowers installation and workflow preconditions |

## Templates And Workflows

The full template and workflow catalog is in [en/agentOperatingKit.md](en/agentOperatingKit.md).

This README covers only the project overview and quick start. When an agent applies AOK, it should use `en/agentOperatingKit.md` as the source index and read only the selected template or workflow files needed for the chosen scope.

Workflow templates are provided only for projects that use Superpowers.

## Relationship to DESIGN.md

AOK's optional `DESIGN.md` template follows the DESIGN.md format introduced by [Google Stitch](https://stitch.withgoogle.com/docs/design-md/specification) and specified in [google-labs-code/design.md](https://github.com/google-labs-code/design.md).

AOK's template is an adaptation for AOK's routed-read model. It is not an official Google template, and third-party `DESIGN.md` examples should be treated as references unless the project owner confirms they are official design systems.

## Relationship to Superpowers

AOK workflow templates are written around [Superpowers](https://github.com/obra/superpowers) skills. If you want to use workflow documents, install Superpowers in your LLM environment first.

AOK does not provide converted workflow documents for environments that do not use Superpowers. In that case, AOK provides only the basic root `AGENTS.md` operating guidance.

## License

Released under the MIT No Attribution License (MIT-0). See [LICENSE](LICENSE) for details.

---

# 한국어

Agent Operating Kit(AOK)는 agent와 함께 프로젝트를 운영하기 위한 문서/워크플로우 템플릿 팩입니다.

AOK는 더 큰 프롬프트를 만들기 위한 도구가 아니라, 항상 읽는 agent 지침은 작게 유지하고 필요한 workflow와 프로젝트 지식만 찾아 읽게 만드는 템플릿 팩입니다.

English version: [English](#agent-operating-kit)

## 왜 필요한가

agent와 프로젝트를 오래 같이 운영하다 보면 다음 문제가 자주 생깁니다.

- 기획만 있는 repo에서 개발을 시작하려는데 agent가 무엇부터 봐야 할지 모른다.
- 기능 추가, 버그 수정, 리팩터링, 문서 변경의 작업 파이프라인이 매번 흔들린다.
- agent가 문서를 많이 만들었지만 코드와 문서, 문서와 문서 사이의 기준이 어긋난다.
- `AGENTS.md`나 설계 문서가 너무 커져서 작은 작업에도 컨텍스트를 많이 소모한다.
- 기존 프로젝트에 agent 운영 규칙을 도입하고 싶지만 기존 문서를 잃거나 덮어쓸 위험이 있다.

AOK는 이런 상황에서 프로젝트별 agent 지침, workflow, 문서 지도, 문서 거버넌스 규칙을 작고 명확한 파일로 나누어 적용하게 합니다.

## 핵심 원칙

- 루트 `AGENTS.md`는 매 세션 읽어도 부담 없는 크기로 유지한다. 작은 프로젝트는 50-100줄 안팎을 우선한다.
- 프로젝트에 필요한 구성요소만 선택해 적용한다.
- 사용자에게 필요한 적용 범위를 선택지로 먼저 묻는다.
- 기존 프로젝트 문서는 먼저 읽고, 정보 손실 없이 AOK 구조에 반영한다.
- 기존 문서 이동, 삭제, deprecated/archive 처리는 사용자 승인 후 진행한다.
- 긴 절차는 Superpowers를 사용하는 프로젝트에서만 `.agents/workflows/*.md`로 분리한다.
- Superpowers를 쓰지 않는 프로젝트에는 AOK workflow 문서를 제공하지 않고, 루트 `AGENTS.md`의 기본 작업 원칙만 적용한다.
- `~/.codex/AGENTS.md` 같은 전역 지침은 기본 적용 대상이 아니며, 사용자가 선택한 경우에만 다룬다.

AOK 적용의 성공 기준은 일반 작업에서 agent가 읽어야 하는 기본 컨텍스트가 줄어드는 것이다. AOK를 적용한 결과 모든 작업에서 더 많은 문서를 기본으로 읽게 된다면 적용이 잘못된 것이다.

## 빠른 시작

agent에게 다음처럼 요청합니다.

```text
이 repo에 Agent Operating Kit를 적용하고 싶어.
ko/agentOperatingKit.md를 먼저 읽고, AOK 적용 가이드라인에 따라 나에게 선택지를 제시해줘.
기존 파일은 바로 수정하지 말고 적용안을 먼저 제안해줘.
```

agent는 먼저 [ko/agentOperatingKit.md](ko/agentOperatingKit.md)를 읽고, 필요한 경우 아래 문서를 순서대로 확인합니다.

1. [AOK 적용 가이드라인](ko/aok/application-guide.md)
2. [구성요소 선택 가이드](ko/aok/component-selection.md)
3. [권장 파일 구조](ko/aok/file-structure.md)
4. workflow를 적용할 경우 [Superpowers 설치 및 workflow 적용 전제](ko/aok/superpowers-install.md)
5. 선택한 템플릿 또는 workflow 파일

## 구성요소 선택

AOK는 정해진 단계를 따라 설치하는 도구가 아니라, 프로젝트 상황에 따라 필요한 구성요소만 고르는 템플릿 팩입니다.

| 구성요소 | 쓸 때 |
|---|---|
| 루트 `AGENTS.md` | agent가 항상 알아야 하는 프로젝트 개요, 명령어, 검증 라우팅이 필요할 때 |
| `DESIGN.md` | UI/frontend 작업에서 색상, typography, spacing, component 기준을 반복 설명하지 않게 해야 할 때 |
| 문서 지도 / 지침 거버넌스 섹션 | 문서 source-of-truth 상태나 agent 지침 변경 승인 규칙이 필요할 때 |
| `.agents/INDEX.md` | workflow, 하위 agent 지침, 프로젝트 전용 skill을 색인해야 할 때 |
| `.agents/workflows/*.md` | Superpowers를 사용하고 같은 작업 절차가 반복될 때 |
| ADR / current status / version history | 장기 운영, 문서 정합성, 의사결정 이력 관리가 필요할 때 |
| `docs/work-log.md` | 롤백, 복구, 장애 조사, 회귀 추적에 필요한 과거 흐름을 따로 남겨야 할 때 |

자세한 기준은 [ko/aok/component-selection.md](ko/aok/component-selection.md)를 봅니다.

## 저장소 구조

```text
README.md
ko/
  aok/
  agentOperatingKit.md
en/
  aok/
  agentOperatingKit.md
```

## 주요 문서

| 문서 | 역할 |
|---|---|
| [ko/agentOperatingKit.md](ko/agentOperatingKit.md) | AOK 한국어 인덱스 |
| [ko/aok/application-guide.md](ko/aok/application-guide.md) | 적용 전 사용자 인터뷰, 기존 프로젝트 적용 원칙 |
| [ko/aok/component-selection.md](ko/aok/component-selection.md) | AOK 구성요소 선택 기준 |
| [ko/aok/file-structure.md](ko/aok/file-structure.md) | AOK가 권장하는 파일 구조 |
| [ko/aok/superpowers-install.md](ko/aok/superpowers-install.md) | Superpowers 설치와 workflow 적용 전제 |

## 템플릿과 Workflow

템플릿과 workflow의 전체 카탈로그는 [ko/agentOperatingKit.md](ko/agentOperatingKit.md)에 있습니다.

README는 프로젝트 소개와 빠른 시작만 다룹니다. agent가 실제로 AOK를 적용할 때는 `ko/agentOperatingKit.md`를 원본 인덱스로 읽고, 선택한 범위에 필요한 템플릿이나 workflow 파일만 추가로 확인합니다.

Workflow 템플릿은 Superpowers를 사용하는 프로젝트에만 제공합니다.

## DESIGN.md와의 관계

AOK의 선택 `DESIGN.md` 템플릿은 [Google Stitch](https://stitch.withgoogle.com/docs/design-md/specification)가 도입하고 [google-labs-code/design.md](https://github.com/google-labs-code/design.md)에서 명세한 DESIGN.md 형식을 따른다.

AOK의 템플릿은 AOK의 필요한 문서만 읽는 모델에 맞춘 적용 템플릿이다. 공식 Google 템플릿은 아니며, 제3자 `DESIGN.md` 예시는 프로젝트 소유자가 공식 디자인 시스템이라고 확인한 경우가 아니라면 참고 자료로 취급한다.

## Superpowers와의 관계

AOK의 workflow 템플릿은 [Superpowers](https://github.com/obra/superpowers) 스킬 기반으로 작성되어 있습니다. 따라서 workflow 문서를 쓰려면 먼저 사용하는 LLM 환경에 Superpowers를 설치해야 합니다.

Superpowers를 쓰지 않는 환경에서는 workflow 문서를 변환해 제공하지 않습니다. 이 경우 AOK는 루트 `AGENTS.md` 중심의 기본 운영 지침까지만 제공합니다.

## 라이선스

MIT No Attribution License (MIT-0)로 배포합니다. 자세한 내용은 [LICENSE](LICENSE)를 확인하세요.
