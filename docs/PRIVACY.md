# EmpireCat Privacy Model

EmpireCat should be useful without becoming invasive. The project must be designed around a clear privacy boundary because developer tools can accidentally expose sensitive source code, credentials, client data, and personal activity.

## Core Promise

EmpireCat is local-first by default.

The app should not record typed text, store keystrokes, upload repository code, or send data to an AI provider unless the user explicitly enables and confirms that behavior.

## Allowed Local Signals

EmpireCat may use these signals locally:

- Selected repository path
- Git branch name
- Number of changed files
- Number of staged files
- Number of untracked files
- Last commit message and SHA
- Test command status when user configures it
- App settings and mascot preferences

These signals are enough to power a useful repo-health companion without hidden surveillance.

## Disallowed Hidden Collection

EmpireCat must not silently collect or store:

- Raw typed text
- Keystroke history
- Passwords
- Environment variables
- Private keys
- `.env` contents
- Full source files
- Full diffs
- Clipboard contents
- Browser history
- Chat logs

## AI Request Rules

AI features must follow these rules:

1. AI is disabled by default.
2. The user must configure a provider/API key before use.
3. The app must show a preview of the payload before sending.
4. The app must clearly mark whether diffs or file contents are included.
5. The user must be able to cancel before sending.
6. Every request should be logged in an audit trail.
7. The audit trail should record metadata and payload summary, not secrets.

## Example Safe AI Payload

```json
{
  "task": "generate_commit_message",
  "repo": "EmpireCat",
  "branch": "feature/repo-watcher",
  "changedFiles": [
    "src/features/repo/repoStore.ts",
    "src-tauri/src/commands/git.rs"
  ],
  "diffIncluded": false,
  "userConfirmed": true
}
```

## Example Unsafe Payload

```json
{
  "fullRepositoryUpload": true,
  "envFiles": [".env"],
  "clipboard": "hidden clipboard text",
  "typedTextHistory": "captured keyboard data"
}
```

This must never be sent.

## User Controls

Planned controls:

- Enable/disable AI features
- Select AI provider
- Require confirmation before every AI request
- Include/exclude diffs
- Clear audit log
- Disable activity signals
- Disable autostart
- Reset all local data

## Interview Talking Point

The privacy model is part of the product architecture. EmpireCat intentionally uses repo metadata and user-triggered commands instead of hidden input capture. This shows product judgment, security awareness, and respect for developer trust.
