# Superpowers Installation and Workflow Preconditions

AOK workflow templates are written around Superpowers skills. Projects that apply workflow documents must first install Superpowers in the relevant LLM environment.

If Superpowers is not installed or not used, do not provide `.agents/workflows/*.md`. In that case, AOK applies only the short root `AGENTS.md` operating guidance and any explicitly selected document routing.

Do not create workflow documents that translate skill calls into generic procedures, checklists, or tool names. AOK workflow quality assumes the availability of Superpowers skill calls.

Installation methods can change, so always check the latest official README and installation docs at the time of application.

Official repository:

- https://github.com/obra/superpowers

## Superpowers Usage Signals

When applying AOK to an existing project, use these signals if Superpowers usage is unclear.

| Judgment | Signals |
|---|---|
| Likely used | `docs/superpowers/`, `.superpowers/`, `AGENTS.md` with Superpowers skill names, spec/plan/review outputs, skill calls such as `brainstorming`, `writing-plans`, `test-driven-development`, or `verification-before-completion` |
| Needs confirmation | Superpowers is not named, but agent plans, specs, reviews, or workflow documents appear repeatedly and look skill-based |
| Treat as unused | No related outputs or skill calls exist, and the user says they do not want to install or use Superpowers |

Even when Superpowers is likely used, do not create workflows immediately. Confirm whether the user wants to keep using Superpowers, then create only approved workflows.

## Environment-Specific Installation

### Claude Code

Using the official marketplace:

```bash
/plugin install superpowers@claude-plugins-official
```

Using a separate marketplace:

```bash
/plugin marketplace add obra/superpowers-marketplace
/plugin install superpowers@superpowers-marketplace
```

### Cursor

Run in Cursor Agent chat:

```text
/add-plugin superpowers
```

Or search for `superpowers` in the plugin marketplace.

### Codex

#### Codex CLI

Open the plugin search interface:

```bash
/plugins
```

Search for `superpowers`, then choose `Install Plugin`.

#### Codex App

Open Plugins in the Codex App sidebar, then click `+` next to `Superpowers` in the Coding section.

#### Manual Installation / Fallback

If automatic installation is difficult, ask Codex to fetch and follow the official installation document:

```text
Fetch and follow instructions from https://raw.githubusercontent.com/obra/superpowers/refs/heads/main/.codex/INSTALL.md
```

If manual installation is required, follow the official Codex instructions.

```bash
git clone https://github.com/obra/superpowers.git ~/.codex/superpowers
mkdir -p ~/.agents/skills
ln -s ~/.codex/superpowers/skills ~/.agents/skills/superpowers
```

On Windows, use a junction instead of a symlink if needed.

```powershell
New-Item -ItemType Directory -Force -Path "$env:USERPROFILE\.agents\skills"
cmd /c mklink /J "$env:USERPROFILE\.agents\skills\superpowers" "$env:USERPROFILE\.codex\superpowers\skills"
```

If an older bootstrap-based installation exists, check the official installation document for removal steps and avoid duplicate loading.

After installation, restart Codex and verify that the skill path is connected.

```bash
ls ~/.agents/skills/superpowers
```

On Windows:

```powershell
Get-ChildItem "$env:USERPROFILE\.agents\skills\superpowers"
```

To update a manual installation, update the official repository and start a new session.

```bash
cd ~/.codex/superpowers
git pull
```

Codex may need multi-agent support enabled to use subagent-based skills such as `dispatching-parallel-agents` and `subagent-driven-development`.

```toml
[features]
multi_agent = true
```

### OpenCode

Ask OpenCode to fetch and follow the official installation document:

```text
Fetch and follow instructions from https://raw.githubusercontent.com/obra/superpowers/refs/heads/main/.opencode/INSTALL.md
```

Or add the plugin to `opencode.json`:

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

Update:

```bash
gemini extensions update superpowers
```

### Installation Check

Start a new session and ask for something that should trigger a skill:

```text
help me plan this feature
```

Or:

```text
let's debug this issue
```

The installation is active if the agent automatically uses the relevant Superpowers skill or can load it through the environment's skill tool.
