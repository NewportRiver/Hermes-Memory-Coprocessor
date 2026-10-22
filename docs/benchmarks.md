# Benchmark Protocol

Compare A: Hermes + Codex alone; B: Hermes + remote memory service; C: Hermes + Pocket Paperclip; D: optional local LLM.

## Metrics
- `MemAvailable`, process RSS, swap use, Android process kills
- Storage use, database size and startup time
- P50/P95 retrieval and task latency
- Task success rate and tool-call correctness
- Network throughput, battery drain and device temperature

## Procedure
1. Record idle baseline after a consistent settling period.
2. Execute the same fixed workload at least 3 times per configuration.
3. Record failures, reconnects, and background app behavior.
4. Avoid comparing results across different models or prompts without labeling changes.
5. Publish anonymized observations; never include API keys or personal files.

## CSV schema
`timestamp,configuration,trial,task,success,latency_ms,phone_mem_available_kib,phone_swap_used_kib,hermes_rss_kib,notes`

## Hypothesis
Offloaded retrieval/database services may improve phone memory headroom, but network latency and power overhead may outweigh benefits for small workloads.
