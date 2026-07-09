# EmpireCat

EmpireCat is a cross-platform AI desktop coding companion for developers. It started as a fork of [ayangweb/BongoCat](https://github.com/ayangweb/BongoCat), then pivots the desktop-pet concept into a serious developer-productivity demo: a local-first mascot that reacts to repo health, focus sessions, Git activity, and optional AI-generated workflow summaries.

The goal is to make this repo interview-ready: fun enough to be memorable, technical enough to show desktop architecture, Rust/Tauri integration, TypeScript product thinking, privacy discipline, and AI workflow design.

## Product Vision

EmpireCat sits on the desktop as a lightweight animated companion. Instead of tracking private keystrokes, it listens for safe development signals and turns them into useful feedback:

- Current Git branch and working-tree state
- Changed file count and last commit context
- Optional test/build status
- Optional GitHub issue or pull-request context
- Focus-session nudges
- AI-assisted commit-message drafts and repo summaries

EmpireCat should never be a hidden keylogger or surveillance tool. The product rule is simple: local-first by default, no typed text capture, no code upload unless the user explicitly opts in.

## Why This Is Different From BongoCat

BongoCat is a cute interactive desktop pet. EmpireCat keeps the delightful desktop companion foundation but turns the project into a developer workflow assistant.

| Area | BongoCat Foundation | EmpireCat Direction |
|---|---|---|
| Core experience | Animated desktop pet | AI coding companion |
| Input model | Keyboard/mouse/controller reactions | Privacy-safe activity and repo signals |
| User value | Fun desktop interaction | Developer productivity and workflow awareness |
| Technical story | Tauri + Vue + Rust desktop app | Tauri + Vue + Rust + Git/GitHub/AI architecture |
| Interview angle | Forked open-source app | Productized and re-architected developer tool |

## Planned MVP

### Phase 1 — Rebrand and Foundation

- Rename product metadata to EmpireCat
- Replace README with product/architecture story
- Add architecture, privacy, and roadmap docs
- Keep MIT license attribution from the upstream project

### Phase 2 — Local Developer Signals

- Add a local repo selector
- Read branch name and working-tree state
- Count changed files without uploading file contents
- Surface a small repo-health card in the desktop window

### Phase 3 — Command Panel

- Add global shortcut for a quick command panel
- Commands:
  - Summarize repo status
  - Generate commit message
  - Explain current branch
  - Show next tasks

### Phase 4 — AI Layer

- Add provider-neutral AI adapter
- Build prompts from Git status/diff only when user confirms
- Show an audit log of what data was sent
- Default to disabled until configured

### Phase 5 — GitHub Integration

- Optional GitHub token or app integration
- Pull issue and PR context
- Summarize open review work
- Link mascot states to repo events

## Architecture

```text
EmpireCat
├── Desktop Shell
│   ├── Tauri windowing
│   ├── transparent always-on-top mascot window
│   └── preference/settings window
├── Frontend
│   ├── Vue 3
│   ├── TypeScript
│   ├── Pinia state
│   └── animated mascot components
├── Rust Backend
│   ├── safe command wrappers
│   ├── Git status service
│   ├── filesystem access controls
│   └── system integrations
├── Intelligence Layer
│   ├── repo signal normalizer
│   ├── rule-based nudges
│   ├── optional AI summary adapter
│   └── prompt/audit log
└── Integrations
    ├── local Git
    ├── GitHub
    ├── global shortcut
    └── autostart
```

## Tech Stack

- Tauri 2 desktop shell
- Rust backend commands
- Vue 3 frontend
- TypeScript
- Pinia state management
- Vite build system
- UnoCSS / Ant Design Vue family from the upstream project
- Optional AI provider adapter
- Optional GitHub integration

## Run Locally

```bash
pnpm install
pnpm tauri dev
```

If the Tauri CLI is not available globally, use:

```bash
pnpm tauri dev
```

## Interview Pitch

> I forked a popular Tauri desktop-pet app and began converting it into EmpireCat, a local-first AI desktop companion for developers. The redesign keeps the cross-platform Tauri/Vue/Rust foundation but changes the product from entertainment into a developer workflow assistant. The architecture separates the desktop shell, local system signals, repo intelligence, AI summaries, and privacy controls so the app can grow into a serious engineering productivity tool.

## Privacy Principles

- No hidden keylogging
- No storing typed text
- No background code upload
- Local-first repo analysis
- Explicit opt-in for AI requests
- Visible audit trail for every AI summary
- Clear settings for data permissions

See [`docs/PRIVACY.md`](docs/PRIVACY.md) for the full privacy model.

## Roadmap

See [`docs/ROADMAP.md`](docs/ROADMAP.md) for the implementation plan.

## Upstream Credit

This project began as a fork of [ayangweb/BongoCat](https://github.com/ayangweb/BongoCat). The upstream project is licensed under the MIT License, and the original copyright notice is preserved in [`LICENSE`](LICENSE).

## License

MIT License. See [`LICENSE`](LICENSE).
