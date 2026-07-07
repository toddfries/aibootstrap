# aibootstrap Central Knowledge Index

**Last updated:** 2026-07-07T07:42:00Z (initial release)

This file is the single source of truth for what has changed in the central knowledge store. Agents compare the latest entry against their local `.grok/session-state.md` to decide what (if anything) to ingest via the delta protocol in `load-protocol.md`.

## Change Log (newest first)

- **2026-07-07**: Initial release of the aibootstrap seed.
  - Added `behavior.md` (core behavioral primitives)
  - Added `values.md` (pointer to shared values / LOVE.md)
  - Added `load-protocol.md` (delta ingestion rules + future RAG note)
  - Added `AI-CRIBNOTES-seed.txt` (project-agnostic starting crib notes)
  - Created this `index.md`

## How to add a new entry (human or AI when explicitly told)
1. Make the actual changes to the relevant files in `aibootstrap/`.
2. Append a new bullet at the top of the Change Log above with:
   - ISO timestamp
   - One-line summary of what changed and why it matters
3. (Optional) If the change is large or needs more explanation, create a dated file in `changes/` and reference it.

Agents should never edit this file except when following an explicit "update central index" instruction after making approved central changes.