# QA media for getpaseo/paseo#6075

Recordings, screenshots and CLI transcripts for the Claude Plan and Bypass report. Captured with a
real Claude Code 2.1.285 agent (Agent SDK 0.3.246) on an isolated Paseo daemon (Linux, web app in
headless Chromium) with a stdio MCP server whose only tool, `search_docs`, has no annotations.

## before/ (Paseo 0.11.0-beta.3, main at 97083dd, before the fix)

- `web/recording.webm`: the whole flow below.
- `web/01-bypass-selected.png`: a Claude agent in Bypass.
- `web/02-mode-menu.png`: the mode menu lists Plan Mode next to Bypass.
- `web/03-plan-mode-replaces-bypass.png`: selecting Plan replaces Bypass in the picker.
- `web/04-permission-card-in-plan.png`: the MCP call asks for approval while planning.
- `web/05-after-deny.png`: the card after answering it.
- `cli/`: the same reproduction through the CLI (`paseo run`, `agent mode`, `permit ls`, `agent inspect`).
