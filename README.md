# aibootstrap

Central, versioned source of shared agent behavior, values, and bootstrapping knowledge for all projects.

## Quick start for a new project
1. Copy `AI-CRIBNOTES-seed.txt` into your project as `.grok/AI-CRIBNOTES.txt` (or similar).
2. Create `.grok/session-state.md` with initial content (e.g. `last_central_update: 1970-01-01`).
3. On first serious session, follow the delta ingestion protocol in `load-protocol.md`.

## Philosophy
- Small, stable behavioral core (`behavior.md`) that almost never changes.
- Delta ingestion so projects only pay token cost for actual new knowledge.
- Local per-project `AI-CRIBNOTES.txt` grows with real operational wisdom.
- Future-proof path to vector database RAG when volume grows large (see `load-protocol.md`).

Human (or explicitly instructed AI) maintains this directory. Projects opt-in to updates via the documented protocol.