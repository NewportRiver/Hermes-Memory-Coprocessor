# Pocket Paperclip — Android Feasibility

## Goal
Run a disposable, single-agent Paperclip organization alongside Android Hermes, separate from the Newport River production company.

## Prerequisites to verify
- Node/npm versions and supported CPU architecture
- Native dependencies and database compatibility with Termux
- Available memory, swap behavior, and free storage
- Local dashboard access and Android background process limits

## Initial configuration
- One CEO agent using existing Hermes/Codex inference
- Test organization, test credentials and separate database
- Bind local dashboard to loopback only
- No automatic access to production Paperclip or corporate memory

## Validation
1. Paperclip service starts and stays running.
2. Dashboard loads in phone browser.
3. One task is created, executed and logged.
4. Service restarts without losing data.
5. Android stays responsive and no data corruption occurs.

## Alternative
If native Android installation fails, host Paperclip on a companion Linux machine while Hermes and dashboard remain on the phone. This is a distributed experiment, not a local install.

**Status:** Not installed or validated.
