# Codex Handoff

This run reached live Codex execution, but Codex did not finish successfully.

- Reason: codex_idle_after_90s
- Mode: live
- Project ID: proj-1
- Namespace mount root during the run: /tmp/tmp.ppN87x61eZ/mount
- Writable project path inside the mount: /tmp/tmp.ppN87x61eZ/mount/nodes/local/fs
- Namespace metadata directory: /tmp/tmp.ppN87x61eZ/mount/meta
- Project metadata directory: /tmp/tmp.ppN87x61eZ/mount/projects/proj-1/meta
- Remote shared-data directory: /tmp/tmp.ppN87x61eZ/mount/shared_data
- Codex auth mode selected: existing_login
- Codex binary: /tmp/tmp.ppN87x61eZ/codex-runtime/npm-prefix/node_modules/.bin/codex
- Codex stdout log: /tmp/spiderweb-external-codex-matrix2/v0.110.0-json-no-pty/logs/codex.stdout.log
- Codex stderr log: /tmp/spiderweb-external-codex-matrix2/v0.110.0-json-no-pty/logs/codex.stderr.log
- Codex PTY transcript: /tmp/spiderweb-external-codex-matrix2/v0.110.0-json-no-pty/logs/codex.pty.log

- Codex JSON events captured: true
- Codex event count: 7
- Last observed event: item.completed
- Last completed item: agent_message
- Inferred stall stage: after_agent_message
- Last agent message: I have the service mount picture now. I’m pulling the rest of the ordered inputs so I can map the exact 10 locations, 10 items, and puzzle definitions into the game state without extra repo reads.

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
