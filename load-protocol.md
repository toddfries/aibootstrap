# Delta Ingestion Protocol (token-efficient knowledge loading)

This protocol ensures the agent receives updates from the central `aibootstrap/` store without repeatedly reading the entire knowledge base.

## Normal Session Start (cheap path)
1. Read `aibootstrap/behavior.md` (the behavioral primitives — small and stable).
2. Read `aibootstrap/values.md` (or follow its pointer to LOVE.md / equivalent).
3. Read `aibootstrap/index.md` and extract the latest timestamp or change hash.
4. Compare against the timestamp/hash recorded in the project's local `.grok/session-state.md`.
5. If nothing new since last recorded state → proceed with existing local knowledge. Done (very low token cost).
6. If there are new entries since last state:
   - Read only the changed or new sections referenced in `index.md`.
   - Merge relevant new intel into the local `AI-CRIBNOTES.txt` (add a short "Sourced from central on YYYY-MM-DD" note).
   - Update `.grok/session-state.md` with the new latest timestamp/hash.
7. Optional but recommended on first session in a project or after significant central changes: run a quick "Values & Behavior Alignment" micro-check before generating proposals.

## Human-triggered full sync
When the human says "sync central knowledge", "ingest latest aibootstrap updates", or similar:
- Force re-read of `index.md`.
- Process all entries newer than the local state (even if some were previously skipped).
- Update local crib notes and session-state.
- Optionally re-run any affected regress tests.

## Future evolution: Vector Database RAG
When the total volume of central + local crib notes grows large (many projects, hundreds of captured gotchas, long playbooks), file-based delta reading becomes less efficient.

**What Vector Database RAG is:**
Instead of the agent reading whole files or large sections, all knowledge is broken into small "chunks" (paragraphs, rules, gotchas, examples). Each chunk is converted into a high-dimensional vector (embedding) that captures its semantic meaning. These vectors are stored in a vector database (Chroma, FAISS, Pinecone, Weaviate, or even a local SQLite + embeddings extension).

When the agent needs context for a task (e.g. "analyze this low-funds + multipart failure pattern"), it creates an embedding of the current query/context and performs a fast similarity search in the vector database. It retrieves only the top-k most semantically relevant chunks — often just a few hundred tokens instead of thousands.

**Why it is relevant here:**
- Perfect next step after the file-based delta protocol you are starting with.
- Scales gracefully as `aibootstrap/` and per-project crib notes accumulate real operational wisdom.
- Enables semantic search ("find all captured patterns related to collateral lockup or quorum failures") instead of brittle filename or keyword matching.
- Can be implemented incrementally: start with the current file + index system, then add an embeddings + vector store layer later without throwing away the existing structure.
- Keeps token usage low even when the "AI bible" becomes genuinely large.

The current delta + index protocol is the correct lightweight foundation that makes a future RAG upgrade straightforward and low-risk.

## Rules for central updates
- Human (or explicitly instructed AI) edits `aibootstrap/` files.
- After changes, update `index.md` with a new timestamped entry describing what changed and why (one line is usually enough).
- The protocol above ensures no project is forced to ingest changes until it chooses to (or the human triggers a sync).