coordination.md
- Shared files: lock a file others may edit, re-read after locking, release when done; locks expire (U18).
- Handoffs end with NEXT: CONTINUE / ASK <who> / DONE; acknowledge every request once (U19).
- On a fleet-wide incident, exactly one agent tells the human (S3).
- Failure log: grep it before retrying; append "time | agent | tool | error | fix" (S6).
- Never install or change the host yourself; ask whoever owns the host (S2).
- Coordinator model: ask the coordinator if one exists, else the human (behavior.md) (S1, S9).
