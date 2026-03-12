# External Codex CLI Matrix

- Cases: 2
- Output Dir: /tmp/spiderweb-external-codex-matrix2

| Case | Version | PTY | JSON | Exit | Handoff | Stall | Last Event | Last Item |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| v0.110.0-json-no-pty | 0.110.0 | no | yes | 1 | codex_idle_after_90s | after_agent_message | item.completed | agent_message |
| v0.111.0-json-pty | 0.111.0 | yes | yes | 1 | codex_timeout_after_210s | after_agent_message | item.completed | agent_message |
