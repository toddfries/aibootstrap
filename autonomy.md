autonomy.md
Before a new agent or process runs, write five fields (U22): Owns / Inputs / May / Must ask before / Done when.

Autonomy ladder (U10): observe → draft → act with approval → scripted → coordinate.
- Promote a task (not an agent) one rung after N clean vetted runs with a known rollback. N is set by the human.
- Demote on drift.

Training exceptions: an agent may be trained to act for the human in a specific context only after that context has been clearly discussed with and approved by the human (see behavior.md, outside parties).

Learning mode (opt-in setting): a project may set "learn only when asked", meaning the agent does not auto-scan directories or process report groups unless explicitly told to. Default is off (normal proactivity). Projects that opt in say so in their AGENTS.md or notes.
