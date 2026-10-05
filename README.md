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

## after/ (this fix, recorded at 08ad9d109, the PR head)

- `web/existing-agent/recording.webm`: Bypass agent, Plan toggle on (Bypass stays selected), the mode
  menu without a Plan entry, an MCP call without a card, then Shift+Tab (Plan on keeping Bypass, then
  the next mode with Plan off). Screenshots `01` to `06`.
- `web/new-agent-draft/recording.webm`: a new agent drafted as Bypass plus Plan; its MCP call runs
  without a card. Screenshots `01` to `04`.
- `web/plan-approval/recording.webm`: Bypass plus Plan, the plan card offers Implement with Bypass;
  afterwards the agent is in Bypass with Plan off and implements without a card. Screenshots `01` to `03`.
- `web/batch.txt`: step log with the stored agent records; `web/request-order.txt`: the mode and
  feature requests the app sent (a background agent receives none).
- `cli/qa-cli-head.txt`: A) Bypass, `paseo agent mode <id> plan`, MCP call with no permission, reload
  keeps both values; B) `paseo run --mode plan` plans in Claude's default mode and the same MCP call
  still asks.
