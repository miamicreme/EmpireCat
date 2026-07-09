# EmpireCat Roadmap

This roadmap turns the BongoCat fork into an interview-ready developer productivity app without trying to rewrite everything at once.

## Milestone 0 — Fork Cleanup

Status: started.

- [x] Rename repository to EmpireCat
- [x] Update package metadata
- [x] Update Tauri product metadata
- [x] Replace README with EmpireCat positioning
- [x] Add architecture documentation
- [x] Add privacy documentation
- [ ] Update screenshots/branding assets
- [ ] Verify local build on Windows

## Milestone 1 — Local Repo Intelligence

Goal: show useful repo status without AI.

Tasks:

- [ ] Add repo selector in preferences
- [ ] Store selected repo path locally
- [ ] Add Rust command for `git status --porcelain`
- [ ] Add Rust command for current branch
- [ ] Add Rust command for last commit summary
- [ ] Normalize results into `RepoSignalSnapshot`
- [ ] Add `RepoStatusCard.vue`
- [ ] Map repo state to mascot mood

Acceptance criteria:

- User can select a local repo.
- App shows branch and changed-file count.
- Mascot enters attention state when repo has uncommitted changes.
- No file contents are read or uploaded.

## Milestone 2 — Command Panel

Goal: make the app feel like a real developer tool.

Tasks:

- [ ] Add global shortcut for command panel
- [ ] Add command palette UI
- [ ] Add command: summarize repo status
- [ ] Add command: suggest next action
- [ ] Add command: draft commit message from file names
- [ ] Add command history

Acceptance criteria:

- User can open command panel from keyboard.
- Commands run from local repo signals.
- No AI provider is required for basic summaries.

## Milestone 3 — AI Summary Layer

Goal: optional AI assistance with a visible privacy boundary.

Tasks:

- [ ] Add AI provider settings
- [ ] Add provider-neutral interface
- [ ] Add prompt builder
- [ ] Add payload preview modal
- [ ] Add request audit log
- [ ] Add commit-message generation
- [ ] Add repo-status summary

Acceptance criteria:

- AI is off by default.
- User sees the exact data payload before sending.
- Audit log records every AI request.
- User can generate a commit message from repo metadata.

## Milestone 4 — GitHub Context

Goal: connect local work to GitHub issues and PRs.

Tasks:

- [ ] Add GitHub integration settings
- [ ] Fetch open issues for selected repo
- [ ] Fetch open PRs for selected repo
- [ ] Link branch name to issue/PR context
- [ ] Add PR review reminder state
- [ ] Add GitHub card to command panel

Acceptance criteria:

- User can see open GitHub work related to the repo.
- App does not require GitHub integration for local mode.

## Milestone 5 — Release Candidate

Goal: produce a polished demo build.

Tasks:

- [ ] Replace upstream visual branding
- [ ] Add screenshots/GIF to README
- [ ] Add GitHub Actions build workflow
- [ ] Add Windows build artifact
- [ ] Add release notes
- [ ] Add demo script for interviews

Acceptance criteria:

- Repo runs locally.
- README explains the architecture clearly.
- App has an obvious demo path in under five minutes.

## Demo Script

1. Launch EmpireCat.
2. Select a local repo.
3. Show branch and changed files.
4. Make a small code change.
5. Mascot reacts to uncommitted work.
6. Open command panel.
7. Generate local repo summary.
8. Show privacy settings.
9. Explain how AI would be enabled but is off by default.

## Interview Framing

EmpireCat shows:

- Product thinking
- Cross-platform desktop engineering
- Rust/Tauri integration
- Vue/TypeScript architecture
- Local-first privacy model
- AI workflow design
- Git/GitHub developer tooling
