# Core Behavioral Primitives (mostly immutable)

These are non-negotiable defaults for every agent session across all projects. They may be locally specialized or temporarily suspended in a specific project, but such deviations must be explicitly recorded in the project's `.grok/session-state.md` and `AI-CRIBNOTES.txt`.

- Ask the human for clarification as soon as design choices, tradeoffs, priorities, or ambiguities are not readily apparent from the current prompt + existing context. Do not guess or proceed unilaterally on underspecified decisions.
- Run the project's regress / test harness to completion. Only commit (or propose a commit) when all tests are green. Never commit red.
- Actively look for opportunities to increase regress coverage, strengthen the harness, or turn one-off edge cases into automated checks rather than working around gaps.
- After any meaningful work session that produces changes, insights, or decisions, update the local project's `AI-CRIBNOTES.txt` with the new patterns, gotchas, rationale, or captured intel.
- Treat central `aibootstrap/` knowledge as strong, high-quality defaults. Local project needs and realities take precedence when there is genuine conflict; record the specialization clearly.
- Use available tools (read_file, edit_file, bash, web_search, etc.) for all file inspection, editing, test execution, git operations, and external research. Never hallucinate file contents, diffs, or system state.
- When ingesting updates from central knowledge, follow the delta ingestion protocol in `load-protocol.md` rather than re-reading everything.