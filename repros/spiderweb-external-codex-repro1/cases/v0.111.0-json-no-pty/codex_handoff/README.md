# Codex Handoff

This run reached live Codex execution, but Codex did not finish successfully.

- Reason: codex_timeout_after_210s
- Mode: live
- Project ID: proj-1
- Namespace mount root during the run: /tmp/tmp.2gKhz8ZJR9/mount
- Writable project path inside the mount: /tmp/tmp.2gKhz8ZJR9/mount/nodes/local/fs
- Namespace metadata directory: /tmp/tmp.2gKhz8ZJR9/mount/meta
- Project metadata directory: /tmp/tmp.2gKhz8ZJR9/mount/projects/proj-1/meta
- Remote shared-data directory: /tmp/tmp.2gKhz8ZJR9/mount/shared_data
- Codex auth mode selected: existing_login
- Codex binary: /home/deano/.npm-global/bin/codex
- Codex stdout log: /tmp/spiderweb-external-codex-matrix1/v0.111.0-json-no-pty/logs/codex.stdout.log
- Codex stderr log: /tmp/spiderweb-external-codex-matrix1/v0.111.0-json-no-pty/logs/codex.stderr.log
- Codex PTY transcript: /tmp/spiderweb-external-codex-matrix1/v0.111.0-json-no-pty/logs/codex.pty.log

- Codex JSON events captured: true
- Codex event count: 12
- Last observed event: item.completed
- Last completed item: command_execution
- Inferred stall stage: after_tool_result
- Last agent message: I have the exact ten locations, ten items, and three puzzle identities now. I’m doing one small targeted metadata check for workspace/service fields that got truncated, then I’ll write `game.py`, `game_manifest.json`, `w

Rerun a strict live test with the default launcher:

```bash
CODEX_MODE=live \
CODEX_AUTH_MODE=api_key \
OPENAI_API_KEY=... \
bash test-env/test-external-codex-workspace.sh
```

Optional custom launch templates may use these placeholders:

- `{codex_bin}`
- `{workspace_root}`
- `{namespace_root}`
- `{namespace_meta_dir}`
- `{project_meta_dir}`
- `{shared_data_dir}`
- `{prompt_file}`
- `{artifact_dir}`

If you need the temporary environment to stay live for a manual handoff, rerun with `KEEP_TEMP=1`.
