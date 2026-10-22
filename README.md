# Hermes Memory Coprocessor

> **Original research credit:** This project draws inspiration from **Dmitry Grinberg's ROMRAM** RP2040 external-memory experiment. See [CREDITS.md](CREDITS.md) for attribution and original sources. This is an independent Newport River research project, not an official ROMRAM release.

Experimental hardware and software research for extending the *effective working capacity* of Android-hosted Hermes agents through an external memory/compute companion.

> **Research status:** Concept / feasibility. A USB peripheral cannot normally add directly addressable physical RAM to a stock Samsung Galaxy A37. This project investigates offloading, not a promised RAM upgrade.

## Reference test platform
- Samsung Galaxy A37, 6 GB advertised RAM, 128 GB internal storage
- Termux with Hermes agent; Codex cloud inference initially
- Observed baseline: ~5.3 GiB RAM visible, ~1.0 GiB available, 8 GiB swap (backing type unverified), ~22 GiB free storage
- Optional local Qwen inference and isolated Pocket Paperclip experiment

## Research tracks
1. **Baseline:** record Android memory pressure, Termux resource use, swap backing, battery and thermal behavior.
2. **USB/network companion:** prototype a Raspberry Pi-class device running memory-backed cache and API services over USB networking or Wi-Fi.
3. **Agent memory offload:** compare local vs remote retrieval, SQLite-backed storage, and persistent memory synchronization.
4. **Paperclip lab:** test a *separate* single-agent Paperclip deployment, including remote services where feasible.
5. **Local model:** benchmark small quantized models only after stable baseline measurements.

## Success metrics
- Lower phone-side resident memory or fewer out-of-memory kills
- Task completion and tool-call reliability
- End-to-end retrieval latency, throughput and energy use
- Offline resilience and safe reconnect/synchronization
- Reproducible setup without root or modifications to the production Newport River server

## Safety / scope
- No rooting, custom kernels or destructive partition changes in phase 1.
- No assumption that USB storage or network RAM can become Android system RAM.
- Keep credentials out of Git; use loopback or authenticated encrypted channels.
- Preserve Hermes's existing installation and corporate memory; back up before experiments.
- Treat Android background restrictions and Termux package compatibility as testable risks.

See [architecture](docs/architecture.md), [experiment plan](docs/experiment-plan.md), [benchmarks](docs/benchmarks.md), and [Pocket Paperclip](docs/pocket-paperclip.md).

## Project status
Research scaffolding only; no working hardware prototype is claimed.

## License
TBD. No license is granted until one is selected.
