# Codex Usage Report

- Reliability: issue
- Machine Independence: issue
- Project ID: proj-1
- Mode: live
- Skipped Reason: codex_timeout_after_210s

## Access Summary
- mounted_workspace: 388 accesses
  samples: /tmp/tmp.2gKhz8ZJR9/mount, /tmp/tmp.2gKhz8ZJR9/mount/apply_patch, /tmp/tmp.2gKhz8ZJR9/mount/codex-execve-wrapper
- mounted_remote_node: 3 accesses
  samples: /tmp/tmp.2gKhz8ZJR9/mount/shared_data/world_seed.json, /tmp/tmp.2gKhz8ZJR9/mount/shared_data/items_seed.json, /tmp/tmp.2gKhz8ZJR9/mount/shared_data/puzzle_seed.json
- allowed_local_runtime: 0 accesses
- host_local: 1107 accesses
  samples: /safe/Safe/wizball-codex, /safe, /safe/Safe
- system_runtime: 3387 accesses
  samples: /usr/bin/bash, /etc/ld.so.preload, /etc/ld.so.cache

## Executed Commands
- /usr/bin/bash
- /usr/bin/id
- /usr/bin/run-parts
- /usr/bin/cat
- /home/deano/.npm-global/bin/codex
- /home/deano/.local/bin/node
- /usr/local/bin/node
- /usr/bin/node
- /home/deano/.npm-global/lib/node_modules/@openai/codex/node_modules/@openai/codex-linux-x64/vendor/x86_64-unknown-linux-musl/codex/codex
- /home/deano/.codex/tmp/arg0/codex-arg08tLHvM/git

## Candidate Venom Gaps
- codex_runtime: Plain Codex CLI and/or Node runtime executed locally instead of coming from the mounted Spiderweb environment.
- codex_home: Codex touched host home/config paths even though a home surface was mounted.
- terminal_runtime: Codex executed host shell/coreutils commands even though a terminal surface was mounted.
- git_runtime: Codex used host-local git commands or metadata even though a git surface was mounted.

## Disallowed Writes
- /home/deano/.codex
- /home/deano/.codex/tmp/arg0
- /home/deano/.codex/tmp/arg0/codex-arg0DKiPUN/.lock
- /home/deano/.codex/tmp/arg0/codex-arg0DKiPUN
- /home/deano/.codex/tmp/arg0/codex-arg0dpgTUl/.lock
- /home/deano/.codex/tmp/arg0/codex-arg08tLHvM
- /home/deano/.codex/tmp/arg0/codex-arg08tLHvM/.lock
- /home/deano/.codex/tmp/arg0/codex-arg08tLHvM/apply_patch
- /home/deano/.codex/tmp/arg0/codex-arg08tLHvM/applypatch
- /home/deano/.codex/tmp/arg0/codex-arg08tLHvM/codex-linux-sandbox
