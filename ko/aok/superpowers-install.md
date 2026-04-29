# Superpowers 설치 및 workflow 적용 전제

AOK의 workflow 템플릿은 Superpowers 스킬 기반으로 작성되어 있다. workflow 문서를 적용하려는 프로젝트에서는 먼저 해당 LLM 환경에 Superpowers를 설치해야 한다.

Superpowers를 설치하지 않거나 사용하지 않는 환경에는 `.agents/workflows/*.md`를 제공하지 않는다. 이 경우 AOK는 짧은 루트 `AGENTS.md`의 기본 작업 원칙과 사용자가 명시적으로 선택한 문서 라우팅까지만 적용한다.

스킬 호출을 일반 절차, 체크리스트, 도구 이름으로 변환한 workflow를 만들지 않는다. workflow 품질은 Superpowers 스킬 호출과 함께 유지하는 것을 전제로 한다.

설치 방법은 변경될 수 있으므로 적용 시점에는 공식 저장소의 최신 README와 설치 문서를 우선 확인한다.

공식 저장소:
- https://github.com/obra/superpowers

## Superpowers 사용 흔적 판단 기준

기존 프로젝트에 AOK를 적용할 때 Superpowers 사용 여부가 불명확하면 다음 순서로 판단한다.

| 판단 | 흔적 |
|---|---|
| 사용 가능성이 높음 | `docs/superpowers/`, `.superpowers/`, Superpowers skill 이름이 들어간 `AGENTS.md`, spec/plan/review 산출물, `brainstorming`, `writing-plans`, `test-driven-development`, `verification-before-completion` 같은 skill 호출 |
| 확인 필요 | Superpowers 이름은 없지만 agent plan, spec, review 문서가 반복적으로 있고 workflow가 skill 기반처럼 작성되어 있음 |
| 미사용으로 간주 | 관련 산출물과 skill 호출이 없고, 사용자가 설치하지 않겠다고 답함 |

사용 가능성이 높아도 workflow를 바로 만들지 않는다. 먼저 사용자에게 Superpowers를 계속 사용할지 확인하고, 승인된 workflow만 생성한다.

## Superpowers 환경별 설치 방법

### Claude Code

공식 marketplace 사용:

```bash
/plugin install superpowers@claude-plugins-official
```

별도 marketplace를 등록해 설치하는 방식:

```bash
/plugin marketplace add obra/superpowers-marketplace
/plugin install superpowers@superpowers-marketplace
```

### Cursor

Cursor Agent chat에서 실행한다.

```text
/add-plugin superpowers
```

또는 plugin marketplace에서 `superpowers`를 검색해 설치한다.

### Codex

#### Codex CLI

plugin 검색 인터페이스를 연다.

```bash
/plugins
```

`superpowers`를 검색한 뒤 `Install Plugin`을 선택한다.

#### Codex App

Codex App의 sidebar에서 Plugins를 열고, Coding 섹션의 `Superpowers` 옆 `+`를 눌러 설치한다.

#### 수동 설치 / fallback

자동 설치가 어렵다면 Codex에게 공식 설치 문서를 가져와 따르도록 지시한다.

```text
Fetch and follow instructions from https://raw.githubusercontent.com/obra/superpowers/refs/heads/main/.codex/INSTALL.md
```

직접 설치가 필요하면 공식 Codex 문서의 수동 설치 절차를 따른다.

```bash
git clone https://github.com/obra/superpowers.git ~/.codex/superpowers
mkdir -p ~/.agents/skills
ln -s ~/.codex/superpowers/skills ~/.agents/skills/superpowers
```

Windows에서는 symlink 대신 junction을 사용할 수 있다.

```powershell
New-Item -ItemType Directory -Force -Path "$env:USERPROFILE\.agents\skills"
cmd /c mklink /J "$env:USERPROFILE\.agents\skills\superpowers" "$env:USERPROFILE\.codex\superpowers\skills"
```

기존에 bootstrap 방식이나 오래된 설치가 있었다면 공식 설치 문서의 제거 절차를 확인한 뒤 중복 로딩되지 않게 정리한다.

설치 후에는 Codex를 재시작하고, skill 경로가 실제로 연결됐는지 확인한다.

```bash
ls ~/.agents/skills/superpowers
```

Windows에서는 다음처럼 확인할 수 있다.

```powershell
Get-ChildItem "$env:USERPROFILE\.agents\skills\superpowers"
```

수동 설치를 업데이트할 때는 공식 저장소를 최신화한 뒤 새 세션을 시작한다.

```bash
cd ~/.codex/superpowers
git pull
```

Codex에서 `dispatching-parallel-agents`, `subagent-driven-development` 같은 subagent 기반 스킬을 쓰려면 Codex 설정에서 multi-agent 기능이 필요할 수 있다.

```toml
[features]
multi_agent = true
```

### OpenCode

OpenCode에게 공식 설치 문서를 가져와 따르도록 지시한다.

```text
Fetch and follow instructions from https://raw.githubusercontent.com/obra/superpowers/refs/heads/main/.opencode/INSTALL.md
```

또는 `opencode.json`의 `plugin` 배열에 추가한다.

```json
{
  "plugin": ["superpowers@git+https://github.com/obra/superpowers.git"]
}
```

### GitHub Copilot CLI

```bash
copilot plugin marketplace add obra/superpowers-marketplace
copilot plugin install superpowers@superpowers-marketplace
```

### Gemini CLI

```bash
gemini extensions install https://github.com/obra/superpowers
```

업데이트:

```bash
gemini extensions update superpowers
```

### 설치 확인

새 세션을 시작한 뒤, skill이 자동으로 호출될 만한 요청을 한다.

```text
help me plan this feature
```

또는:

```text
let's debug this issue
```

agent가 관련 Superpowers skill을 자동으로 사용하거나, 해당 환경의 skill 도구로 skill을 불러올 수 있으면 설치가 적용된 것이다.
