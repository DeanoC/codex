# External Codex `exec` Stall Repro

## Summary

Codex `exec` stalls during a real Spiderweb-mounted workspace flow before it writes any deliverables.
Across the included cases, Codex never reaches `turn.completed`, never emits the final write step, and never creates the expected game files under the writable mounted workspace.

## Environment

- Repo root: `/safe/Safe/wizball-codex/Spiderweb-finalstack`
- Git commit: `c2b636dd47e3c2ea7e3a02f8a773502c3b82c7ad`
- Git status dirty: `True`
- Host platform: `Linux-6.12.63+deb13-amd64-x86_64-with-glibc2.41`
- Python: `3.13.5`
- Node: `v22.22.0`
- npm: `10.9.4`
- Captured at: `2026-03-12T13:17:56+02:00`

## Scenario

- Linux host installs Spiderweb with the repo-local installer.
- Spiderweb starts with a separate runtime root.
- A clean local `spiderweb-fs-node` is mounted at `/nodes/local/fs`.
- A second standalone node is mounted at `/shared_data`.
- Codex runs via `codex exec` against the mounted workspace with `--skip-git-repo-check`, `--dangerously-bypass-approvals-and-sandbox`, `--ephemeral`, and `--json`.
- The prompt asks Codex to read mounted metadata, consume the shared seed files, and generate `game.py`, `game_manifest.json`, `walkthrough.txt`, and `README.md` under `/nodes/local/fs`.

## Expected

- Codex completes the turn, writes the deliverables, and the validator passes.

## Actual

- Codex emits some early discovery/progress events, then stops.
- No case reaches `turn.completed`.
- No case creates the required game files in the writable mounted workspace.

## Case Matrix

| Case | Version | PTY | JSON | Exit | Handoff | Stall | Last Event | Last Item |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| v0.110.0-json-no-pty | 0.110.0 | no | yes | 1 | codex_idle_after_90s | after_agent_message | item.completed | agent_message |
| v0.111.0-json-no-pty | 0.111.0 | no | yes | 1 | codex_timeout_after_210s | after_tool_result | item.completed | command_execution |
| v0.111.0-json-pty | 0.111.0 | yes | yes | 1 | codex_timeout_after_210s | after_agent_message | item.completed | agent_message |
| v0.112.0-json-no-pty | 0.112.0 | no | yes | 1 | codex_idle_after_90s | after_agent_message | item.started | agent_message |

## Shared Invariants

- All included cases stop before any final write step is visible in the JSON event stream.
- The writable mounted project tree stays at the seeded state only.
- The failure is not limited to a single Codex CLI version.
- PTY wrapping changes the visible stopping point, but does not fix the problem.

## Per-Case Notes

### `v0.110.0-json-no-pty`

- Codex version: `0.110.0`
- PTY: `no`
- Handoff reason: `codex_idle_after_90s`
- Stall stage: `after_agent_message`
- Event count: `7`
- Last event type: `item.completed`
- Last completed item type: `agent_message`
- Last agent message: I have the service mount picture now. I’m pulling the rest of the ordered inputs so I can map the exact 10 locations, 10 items, and puzzle definitions into the game state without extra repo reads.

### `v0.111.0-json-no-pty`

- Codex version: `0.111.0`
- PTY: `no`
- Handoff reason: `codex_timeout_after_210s`
- Stall stage: `after_tool_result`
- Event count: `12`
- Last event type: `item.completed`
- Last completed item type: `command_execution`
- Last agent message: I have the exact ten locations, ten items, and three puzzle identities now. I’m doing one small targeted metadata check for workspace/service fields that got truncated, then I’ll write `game.py`, `game_manifest.json`, `walkthrough.txt`, and `README.md` in one generation step.

### `v0.111.0-json-pty`

- Codex version: `0.111.0`
- PTY: `yes`
- Handoff reason: `codex_timeout_after_210s`
- Stall stage: `after_agent_message`
- Event count: `18`
- Last event type: `item.completed`
- Last completed item type: `agent_message`
- Last agent message: I have the world, item, and puzzle seeds. I’m doing one last tiny metadata extraction for the mount summary, then I’ll write `game.py`, `game_manifest.json`, `walkthrough.txt`, and `README.md` together.

### `v0.112.0-json-no-pty`

- Codex version: `0.112.0`
- PTY: `no`
- Handoff reason: `codex_idle_after_90s`
- Stall stage: `after_agent_message`
- Event count: `8`
- Last event type: `item.started`
- Last completed item type: `agent_message`
- Last started item type: `todo_list`
- Last agent message: I’ve got the exact seeds now: 10 fixed locations, 10 fixed items, 3 named puzzles, and the required victory text. Next I’m writing all four deliverables in one shot with a deterministic map and a walkthrough that solves the game from a clean start.

## Included Artifacts

- `cases/<case>/codex_prompt.txt`
- `cases/<case>/codex_exec_summary.json`
- `cases/<case>/case_summary.json`
- `cases/<case>/logs/codex.stdout.log`
- `cases/<case>/logs/codex.stderr.log`
- `cases/<case>/logs/codex.pty.log` when PTY mode was used
- `cases/<case>/snapshots/*.json` for mounted metadata and Codex runtime snapshot
- `source_summaries/*.json` and `source_summaries/*.md` from the matrix runs

Review host-specific absolute paths before sharing the bundle outside the team.

