# External Codex CLI Matrix

- Cases: 3
- Output Dir: /tmp/spiderweb-external-codex-matrix1

| Case | Version | PTY | JSON | Exit | Handoff | Stall | Last Event | Last Item |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| v0.110.0-json-no-pty | None | no | yes | 1 |  |  |  |  |
| v0.111.0-json-no-pty | 0.111.0 | no | yes | 1 | codex_timeout_after_210s | after_tool_result | item.completed | command_execution |
| v0.111.0-json-pty | None | yes | yes | 1 |  |  |  |  |
