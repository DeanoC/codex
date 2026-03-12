# Codex Handoff

This run reached live Codex execution, but Codex did not finish successfully.

- Reason: codex_timeout_after_210s
- Mode: live
- Project ID: proj-1
- Namespace mount root during the run: /tmp/tmp.ugb45P0RcR/mount
- Writable project path inside the mount: /tmp/tmp.ugb45P0RcR/mount/nodes/local/fs
- Namespace metadata directory: /tmp/tmp.ugb45P0RcR/mount/meta
- Project metadata directory: /tmp/tmp.ugb45P0RcR/mount/projects/proj-1/meta
- Remote shared-data directory: /tmp/tmp.ugb45P0RcR/mount/shared_data
- Codex auth mode selected: existing_login
- Codex binary: /home/deano/.npm-global/bin/codex
- Codex stdout log: /tmp/spiderweb-external-codex-matrix2/v0.111.0-json-pty/logs/codex.stdout.log
- Codex stderr log: /tmp/spiderweb-external-codex-matrix2/v0.111.0-json-pty/logs/codex.stderr.log
- Codex PTY transcript: /tmp/spiderweb-external-codex-matrix2/v0.111.0-json-pty/logs/codex.pty.log

- Codex JSON events captured: true
- Codex event count: 18
- Last observed event: item.completed
- Last completed item: agent_message
- Inferred stall stage: after_agent_message
- Last agent message: I have the world, item, and puzzle seeds. I’m doing one last tiny metadata extraction for the mount summary, then I’ll write `game.py`, `game_manifest.json`, `walkthrough.txt`, and `README.md` together.

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
