# Experiment Plan

## Phase 0 — Baseline
Capture `node -v`, `npm -v`, `uname -m`, `free -h`, `df -h ~`, `cat /proc/swaps`. Record Android version, battery state, temperature (if available), and whether Hermes is idle or running a task. Never publish credentials or personal paths.

## Phase 1 — Server-assisted proof of concept
Run a small authenticated memory service on Architect1 (or another isolated Linux host). Connect Android Hermes over private network. Test read/write, disconnection, reconnect, and measured phone-side memory change.

## Phase 2 — Dedicated hardware
Move the service to a low-power SBC. Compare Wi-Fi and supported USB networking, including power draw and thermal behavior.

## Phase 3 — Pocket Paperclip
Run one isolated Paperclip agent. Validate Node/native dependency support in Termux before attempting installation; compare phone-local vs offloaded database/service architecture.

## Phase 4 — Local LLM
Try a 0.6B–1.7B quantized model with a conservative context size. Benchmark model loading, token throughput, tool-call correctness, and OOM behavior. Keep Codex as control.

## Decision gates
- Stop if repeated Android low-memory kills, severe thermal throttling, or database corruption occurs.
- Advance only when baseline and repeatable results are documented.
- Prefer no-root and reversible changes.

## Initial tasks
- [ ] Confirm Termux Node/npm/CPU architecture
- [ ] Determine swap type and Android memory limits
- [ ] Create sanitized benchmark harness
- [ ] Define memory service protocol
- [ ] Test isolated Paperclip dependencies
- [ ] Prototype external SBC connection
