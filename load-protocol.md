load-protocol.md
Delta ingestion (token supreme):
1. Read behavior.md + values.md + index.md (then other files as index.md routes).
2. Compare index latest timestamp/hash vs local .agent/session-state.md (or the path named in the repo's AGENTS.md).
3. If no newer entries: proceed (minimal tokens).
4. If newer: read only changed sections from index. Merge relevant intel into local AI-CRIBNOTES.txt with "sourced YYYYMMDD" note. Update session-state timestamp.
5. Human says "sync central" or starts big session → force full delta ingest since last state.

Future: when volume large, replace file reads with vector DB RAG (embed chunks, semantic top-k retrieval). Current delta+index is correct lightweight foundation for that upgrade.

Central updates: human (or explicit AI instruction) edits files then appends one-line timestamped entry to index.md Change Log. Projects never auto-ingest; they follow this protocol on next session or explicit sync.
