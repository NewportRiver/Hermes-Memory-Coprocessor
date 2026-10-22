# Proposed Architecture

## Baseline
Galaxy A37 → Termux → Hermes → Codex API. Keep this as the control configuration.

## Companion prototype
Galaxy A37 (Termux / Hermes client)
  ↕ authenticated HTTP over private Wi-Fi or USB networking (if supported)
Companion SBC (Linux)
  ├── memory cache / retrieval API
  ├── optional persistent database
  └── optional inference or background workers

## Distinctions
- External **RAM** on an SBC is owned by the SBC, not Android's kernel.
- External **storage** may hold archives and backups, not safely replace Termux executable storage.
- **Swap** on stock Android is managed by Android; avoid unsupported USB swap modifications.
- Offloading can reduce phone memory usage only when processes/data actually move off-device.

## Candidate hardware
- Existing Architect1 server for zero-cost proof of concept
- Later: Raspberry Pi-class SBC with 4–8GB+ RAM, power and enclosure
- Prefer USB networking when verified; Wi-Fi is the initial fallback

## API sketch (not yet implemented)
- GET /health — version and resource status
- POST /v1/memory/search — retrieve scoped memory
- POST /v1/memory/write — authenticated append with idempotency key
- GET /metrics — resource and latency measurements

## Security
Use least-privilege credentials, authentication, encrypted network links when leaving loopback, no exposed public ports, and scoped memory namespaces. Never copy live corporate secrets into test fixtures.
