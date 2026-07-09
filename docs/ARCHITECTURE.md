# EmpireCat Architecture

EmpireCat is designed as a local-first desktop productivity assistant. The architecture keeps the fun animated mascot separate from the developer-intelligence engine so the app can evolve without turning into a fragile toy fork.

## System Goals

1. Keep the app cross-platform.
2. Preserve the lightweight Tauri desktop experience.
3. Add developer workflow intelligence without invasive monitoring.
4. Make every external AI request explicit and auditable.
5. Keep broker-style integrations modular: Git today, GitHub and AI providers later.

## High-Level Architecture

```text
Frontend Vue App
├── Mascot UI
├── Command Panel
├── Repo Status Card
├── Settings / Privacy Controls
└── Audit Log

Tauri Bridge
├── invoke() commands
├── event bus
├── global shortcuts
└── window controls

Rust Core
├── git_status_service
├── filesystem_guard
├── command_runner
├── settings_service
└── ai_request_audit

Optional Integrations
├── GitHub API
├── AI provider adapter
├── local test runner
└── autostart
```

## Frontend Responsibilities

The frontend should own display, state transitions, and user confirmation.

Planned modules:

- `features/mascot`: mascot state machine and animation mapping
- `features/repo`: repo status store and UI cards
- `features/commands`: command panel and user-triggered actions
- `features/ai`: prompt preview, provider selection, response rendering
- `features/privacy`: permissions, audit log, data visibility

The frontend should not directly run shell commands. It should call typed Tauri commands exposed by Rust.

## Rust Core Responsibilities

The Rust layer should own all local system interaction.

Planned commands:

- `select_repo_path()`
- `get_git_status(path)`
- `get_current_branch(path)`
- `get_changed_file_summary(path)`
- `run_test_command(path, command)`
- `build_ai_payload(request)`
- `write_audit_log(entry)`

Every command should validate paths and avoid broad filesystem access.

## Repo Signal Model

EmpireCat should normalize local developer signals into a small internal object:

```ts
export interface RepoSignalSnapshot {
  repoPath: string
  branch: string
  changedFiles: number
  stagedFiles: number
  untrackedFiles: number
  lastCommitMessage?: string
  lastCommitSha?: string
  testStatus?: 'unknown' | 'passing' | 'failing'
  riskLevel: 'calm' | 'attention' | 'warning'
  capturedAt: string
}
```

The mascot should react to this normalized state instead of directly coupling to Git commands.

## AI Adapter Design

AI support should be provider-neutral.

```ts
export interface AiProvider {
  name: string
  summarizeRepoStatus(input: RepoSummaryInput): Promise<RepoSummaryResult>
  generateCommitMessage(input: CommitMessageInput): Promise<CommitMessageResult>
}
```

Before any AI request, the app should show:

- What data will be sent
- Which provider will receive it
- Whether file diffs are included
- A cancel button

## Privacy Boundary

The app may collect safe signals:

- branch name
- changed file count
- staged/untracked counts
- user-selected repo path
- user-triggered command results

The app must not silently collect:

- typed text
- passwords or secrets
- hidden file contents
- entire repository code
- private diffs without confirmation

## Roadmap-Friendly Boundaries

Keep these modules separate:

- UI state is not Git logic.
- Git logic is not AI logic.
- AI logic is not window logic.
- Privacy/audit logic wraps all AI requests.

This keeps the project explainable in interviews and easier to expand into a real product.
