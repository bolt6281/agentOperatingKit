# Agent Operating Kit

Agent Operating Kit(AOK)는 agent와 함께 프로젝트를 운영하기 위한 문서/워크플로우 템플릿 팩입니다.

AOK는 코드를 대신 작성하는 프레임워크가 아니라, agent가 프로젝트를 읽고, 작업 범위를 판단하고, 문서를 정리하고, 반복 작업 절차를 안정적으로 따르도록 만드는 운영 키트입니다.

English version: [English](#english)

## 왜 필요한가

agent와 프로젝트를 오래 같이 운영하다 보면 다음 문제가 자주 생깁니다.

- 기획만 있는 repo에서 개발을 시작하려는데 agent가 무엇부터 봐야 할지 모른다.
- 기능 추가, 버그 수정, 리팩터링, 문서 변경의 작업 파이프라인이 매번 흔들린다.
- agent가 문서를 많이 만들었지만 코드와 문서, 문서와 문서 사이의 기준이 어긋난다.
- `AGENTS.md`나 설계 문서가 너무 커져서 작은 작업에도 컨텍스트를 많이 소모한다.
- 기존 프로젝트에 agent 운영 규칙을 도입하고 싶지만 기존 문서를 잃거나 덮어쓸 위험이 있다.

AOK는 이런 상황에서 프로젝트별 agent 지침, workflow, 문서 지도, 문서 거버넌스 규칙을 작고 명확한 파일로 나누어 적용하게 합니다.

## 핵심 원칙

- 처음부터 모든 파일을 만들지 않는다.
- 사용자에게 필요한 적용 범위를 선택지로 먼저 묻는다.
- 기존 프로젝트 문서는 먼저 읽고, 정보 손실 없이 AOK 구조에 반영한다.
- 기존 문서 이동, 삭제, deprecated/archive 처리는 사용자 승인 후 진행한다.
- 긴 절차는 Superpowers를 사용하는 프로젝트에서만 `.agents/workflows/*.md`로 분리한다.
- Superpowers를 쓰지 않는 프로젝트에는 AOK workflow 문서를 제공하지 않고, 루트 `AGENTS.md`의 기본 작업 원칙만 적용한다.
- `~/.codex/AGENTS.md` 같은 전역 지침은 기본 적용 대상이 아니며, 사용자가 선택한 경우에만 다룬다.

## 빠른 시작

agent에게 다음처럼 요청합니다.

```text
이 repo에 Agent Operating Kit를 적용하고 싶어.
ko/agentOperatingKit.md를 먼저 읽고, AOK 적용 가이드라인에 따라 나에게 선택지를 제시해줘.
기존 파일은 바로 수정하지 말고 적용안을 먼저 제안해줘.
```

agent는 먼저 [ko/agentOperatingKit.md](ko/agentOperatingKit.md)를 읽고, 필요한 경우 아래 문서를 순서대로 확인합니다.

1. [AOK 적용 가이드라인](ko/aok/application-guide.md)
2. [채택 레벨](ko/aok/adoption-levels.md)
3. [권장 파일 구조](ko/aok/file-structure.md)
4. workflow를 적용할 경우 [Superpowers 설치 및 workflow 적용 전제](ko/aok/superpowers-install.md)
5. 선택한 템플릿 또는 workflow 파일

## 채택 레벨

AOK는 프로젝트 상황에 따라 단계적으로 적용합니다.

| 레벨 | 목적 | 생성 대상 |
|---|---|---|
| Level 1. 최소 적용 | 신규 개발 시작, 작은 프로젝트, 낮은 agent 작업 빈도 | 루트 `AGENTS.md` |
| Level 2. Workflow 적용 | Superpowers 기반 반복 작업 절차 정립 | `AGENTS.md`, `.agents/INDEX.md`, 필요한 workflow |
| Level 3. 문서 거버넌스 적용 | 장기 운영, 문서 정합성 회복, 의사결정 이력 관리 | Level 2 + ADR, current status, version history, 필요한 하위 `AGENTS.md` |
| Custom 적용 | 사용자가 선택한 일부 구성 요소만 적용 | 선택 항목에 따라 결정 |

자세한 기준은 [ko/aok/adoption-levels.md](ko/aok/adoption-levels.md)를 봅니다.

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
| [ko/aok/adoption-levels.md](ko/aok/adoption-levels.md) | Level 1~3, Custom 적용 기준 |
| [ko/aok/file-structure.md](ko/aok/file-structure.md) | AOK가 권장하는 파일 구조 |
| [ko/aok/superpowers-install.md](ko/aok/superpowers-install.md) | Superpowers 설치와 workflow 적용 전제 |

## 템플릿

| 목적 | 파일 |
|---|---|
| 선택 옵션: 전역 Codex 지침 | [ko/aok/templates/global-agents.md](ko/aok/templates/global-agents.md) |
| repo 루트 `AGENTS.md` | [ko/aok/templates/repo-agents.md](ko/aok/templates/repo-agents.md) |
| `.agents/INDEX.md` | [ko/aok/templates/agents-index.md](ko/aok/templates/agents-index.md) |
| Agent 지침 변경 제안 양식 | [ko/aok/templates/agent-change-proposal.md](ko/aok/templates/agent-change-proposal.md) |
| 하위 `AGENTS.md` | [ko/aok/templates/subdir-agents.md](ko/aok/templates/subdir-agents.md) |
| ADR | [ko/aok/templates/adr.md](ko/aok/templates/adr.md) |
| 현재 상태 문서 | [ko/aok/templates/current-status.md](ko/aok/templates/current-status.md) |

## Workflow 템플릿

Workflow 템플릿은 Superpowers를 사용하는 프로젝트에만 제공합니다.

| 작업 유형 | 파일 |
|---|---|
| 기능 추가 / 동작 변경 | [ko/aok/workflows/feature-change.md](ko/aok/workflows/feature-change.md) |
| 버그 수정 | [ko/aok/workflows/bugfix.md](ko/aok/workflows/bugfix.md) |
| 리팩터링 | [ko/aok/workflows/refactor.md](ko/aok/workflows/refactor.md) |
| 문서 / 정책 / ADR 변경 | [ko/aok/workflows/docs-change.md](ko/aok/workflows/docs-change.md) |
| 설정 / 빌드 / CI / 의존성 / 배포 / DB 변경 | [ko/aok/workflows/risky-change.md](ko/aok/workflows/risky-change.md) |
| 조사 / 의사결정 / 기술 선택 | [ko/aok/workflows/research-decision.md](ko/aok/workflows/research-decision.md) |
| 리뷰 피드백 반영 | [ko/aok/workflows/review-feedback.md](ko/aok/workflows/review-feedback.md) |
| 반복 실패 / 프로젝트 전용 스킬화 | [ko/aok/workflows/repeated-failure.md](ko/aok/workflows/repeated-failure.md) |

## Superpowers와의 관계

AOK의 workflow 템플릿은 [Superpowers](https://github.com/obra/superpowers) 스킬 기반으로 작성되어 있습니다. 따라서 workflow 문서를 쓰려면 먼저 사용하는 LLM 환경에 Superpowers를 설치해야 합니다.

Superpowers를 쓰지 않는 환경에서는 workflow 문서를 변환해 제공하지 않습니다. 이 경우 AOK는 루트 `AGENTS.md` 중심의 기본 운영 지침까지만 제공합니다.

## 라이선스

MIT License로 배포합니다. 자세한 내용은 [LICENSE](LICENSE)를 확인하세요.

---

# English

Agent Operating Kit(AOK) is a documentation and workflow template pack for operating software projects with coding agents.

AOK is not a code framework. It is an operating kit that helps an agent understand a project, choose the right workflow, keep project documents aligned, and avoid wasting context on oversized instruction files.

## Why AOK Exists

Projects that use coding agents for real work often run into the same operational problems:

- A repo has planning documents, but no clear path for starting implementation.
- Feature work, bug fixes, refactors, and documentation changes follow inconsistent processes.
- Agent-written documents drift away from code and from each other.
- `AGENTS.md` or planning documents grow too large, wasting context even for small tasks.
- Existing projects need agent operating rules, but blindly replacing old documents risks losing important details.

AOK addresses these problems by splitting agent instructions, workflows, document maps, and governance rules into small files that can be adopted selectively.

## Core Principles

- Do not create the full structure by default.
- Ask the user which parts of AOK they want before applying it.
- Read existing project documents before restructuring them.
- Preserve details and avoid information loss when migrating old documents.
- Ask for approval before moving, deleting, deprecating, or archiving existing files.
- Create `.agents/workflows/*.md` only for projects that use Superpowers.
- If Superpowers is not used, do not provide AOK workflow documents; apply only the basic root `AGENTS.md` operating guidance.
- Treat global instruction files such as `~/.codex/AGENTS.md` as optional.

## Quick Start

Ask your agent:

```text
I want to apply Agent Operating Kit to this repo.
Read en/agentOperatingKit.md first and follow the AOK application guide.
Do not modify existing files immediately. Propose an application plan first.
```

The agent should start with [en/agentOperatingKit.md](en/agentOperatingKit.md), then read only the documents needed for the selected scope:

1. [AOK Application Guide](en/aok/application-guide.md)
2. [Adoption Levels](en/aok/adoption-levels.md)
3. [Recommended File Structure](en/aok/file-structure.md)
4. [Superpowers Installation and Workflow Preconditions](en/aok/superpowers-install.md), if workflows are selected
5. The selected template or workflow files

## Adoption Levels

| Level | Purpose | Typical Files |
|---|---|---|
| Level 1. Minimal Adoption | Small projects, early development, low agent usage | Root `AGENTS.md` |
| Level 2. Workflow Adoption | Superpowers-based repeated work procedures | `AGENTS.md`, `.agents/INDEX.md`, selected workflows |
| Level 3. Documentation Governance | Long-running projects, source-of-truth cleanup, decision history | Level 2 + ADR, current status, version history, selected nested `AGENTS.md` files |
| Custom Adoption | Only the components selected by the user | Depends on the selected scope |

See [en/aok/adoption-levels.md](en/aok/adoption-levels.md) for details.

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
| [en/aok/adoption-levels.md](en/aok/adoption-levels.md) | Level 1, Level 2, Level 3, and custom adoption |
| [en/aok/file-structure.md](en/aok/file-structure.md) | Recommended AOK file structure |
| [en/aok/superpowers-install.md](en/aok/superpowers-install.md) | Superpowers installation and workflow preconditions |

## Templates

| Purpose | File |
|---|---|
| Optional global Codex instructions | [en/aok/templates/global-agents.md](en/aok/templates/global-agents.md) |
| Repo root `AGENTS.md` | [en/aok/templates/repo-agents.md](en/aok/templates/repo-agents.md) |
| `.agents/INDEX.md` | [en/aok/templates/agents-index.md](en/aok/templates/agents-index.md) |
| Agent instruction change proposal | [en/aok/templates/agent-change-proposal.md](en/aok/templates/agent-change-proposal.md) |
| Nested `AGENTS.md` | [en/aok/templates/subdir-agents.md](en/aok/templates/subdir-agents.md) |
| ADR | [en/aok/templates/adr.md](en/aok/templates/adr.md) |
| Current status document | [en/aok/templates/current-status.md](en/aok/templates/current-status.md) |

## Workflow Templates

Workflow templates are provided only for projects that use Superpowers.

| Work Type | File |
|---|---|
| Feature or behavior change | [en/aok/workflows/feature-change.md](en/aok/workflows/feature-change.md) |
| Bug fix | [en/aok/workflows/bugfix.md](en/aok/workflows/bugfix.md) |
| Refactor | [en/aok/workflows/refactor.md](en/aok/workflows/refactor.md) |
| Documentation, policy, or ADR change | [en/aok/workflows/docs-change.md](en/aok/workflows/docs-change.md) |
| Config, build, CI, dependency, deployment, or DB change | [en/aok/workflows/risky-change.md](en/aok/workflows/risky-change.md) |
| Research or technical decision | [en/aok/workflows/research-decision.md](en/aok/workflows/research-decision.md) |
| Review feedback handling | [en/aok/workflows/review-feedback.md](en/aok/workflows/review-feedback.md) |
| Repeated failure or project-specific skill extraction | [en/aok/workflows/repeated-failure.md](en/aok/workflows/repeated-failure.md) |

## Relationship to Superpowers

AOK workflow templates are written around [Superpowers](https://github.com/obra/superpowers) skills. If you want to use workflow documents, install Superpowers in your LLM environment first.

AOK does not provide converted workflow documents for environments that do not use Superpowers. In that case, AOK provides only the basic root `AGENTS.md` operating guidance.

## License

Released under the MIT License. See [LICENSE](LICENSE) for details.
