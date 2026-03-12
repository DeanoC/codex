# Codex Usage Report

- Reliability: issue
- Machine Independence: issue
- Project ID: proj-1
- Mode: live
- Skipped Reason: codex_idle_after_90s

## Access Summary
- mounted_workspace: 278 accesses
  samples: /tmp/tmp.ppN87x61eZ/mount, /tmp/tmp.ppN87x61eZ/mount/apply_patch, /tmp/tmp.ppN87x61eZ/mount/codex-execve-wrapper
- mounted_remote_node: 3 accesses
  samples: /tmp/tmp.ppN87x61eZ/mount/shared_data/world_seed.json, /tmp/tmp.ppN87x61eZ/mount/shared_data/items_seed.json, /tmp/tmp.ppN87x61eZ/mount/shared_data/puzzle_seed.json
- allowed_local_runtime: 81 accesses
  samples: /tmp/tmp.ppN87x61eZ/codex-runtime/npm-prefix/node_modules/.bin/codex, /tmp/tmp.ppN87x61eZ/codex-runtime, /tmp/tmp.ppN87x61eZ/codex-runtime/npm-prefix
- host_local: 881 accesses
  samples: /safe/Safe/wizball-codex, /safe, /safe/Safe
- system_runtime: 2963 accesses
  samples: /usr/bin/bash, /etc/ld.so.preload, /etc/ld.so.cache

## Executed Commands
- /usr/bin/bash
- /usr/bin/id
- /usr/bin/run-parts
- /usr/bin/cat
- /tmp/tmp.ppN87x61eZ/codex-runtime/npm-prefix/node_modules/.bin/codex
- /home/deano/.local/bin/node
- /usr/local/bin/node
- /usr/bin/node
- /tmp/tmp.ppN87x61eZ/codex-runtime/npm-prefix/node_modules/@openai/codex-linux-x64/vendor/x86_64-unknown-linux-musl/codex/codex
- /home/deano/.codex/tmp/arg0/codex-arg0vh44JK/git

## Candidate Venom Gaps
- codex_runtime: Plain Codex CLI and/or Node runtime executed locally instead of coming from the mounted Spiderweb environment.
- codex_home: Codex touched host home/config paths even though a home surface was mounted.
- terminal_runtime: Codex executed host shell/coreutils commands even though a terminal surface was mounted.
- git_runtime: Codex used host-local git commands or metadata even though a git surface was mounted.

## Disallowed Writes
- /home/deano/.codex
- /home/deano/.codex/tmp/arg0
- /home/deano/.codex/tmp/arg0/codex-arg0dpgTUl/.lock
- /home/deano/.codex/tmp/arg0/codex-arg0Ccpz9j/.lock
- /home/deano/.codex/tmp/arg0/codex-arg0Ccpz9j
- /home/deano/.codex/tmp/arg0/codex-arg0vh44JK
- /home/deano/.codex/tmp/arg0/codex-arg0vh44JK/.lock
- /home/deano/.codex/tmp/arg0/codex-arg0vh44JK/apply_patch
- /home/deano/.codex/tmp/arg0/codex-arg0vh44JK/applypatch
- /home/deano/.codex/tmp/arg0/codex-arg0vh44JK/codex-linux-sandbox
