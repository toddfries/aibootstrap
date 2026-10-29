# THREADS.md

Tag threads: a convention for running several topics through one conversation stream.

## Adoption (for the agent reading this cold)

You were pointed here; that is the whole onboarding.

1. Read this file through once. You now hold the convention.
2. Create or locate your own tag tree per "The tag tree" below. This handbook
   holds no tag data, and never will.
3. Confirm adoption in one line, then honor tags from your next reply.
4. `threads on` from the user is the canonical pointer: treat it as the
   instruction to do the three steps above, even mid-conversation.

## Why

Discord and Google Chat have threads. Most agent channels have one stream.
Several topics in queue at once is normal, and in-band labeling is the only
protocol a single stream gives you. This document is that convention, for any
agent, any channel.

## The tag

1. A tag is a short word in square brackets, the first thing on the line:
   `[clouds]`.
2. Lowercase, no spaces or brackets inside. A word that stays right for the
   life of the topic: `[land]`, not `[the-jones-parcel-question]`.
3. The first use is the registration. When the user writes `[tag] ...`, that
   tag exists from that message onward. No ritual, no asking.
4. Both sides carry it. Every message on a thread starts with its tag; the
   agent's replies carry the same tag the user used. A reply that never says
   which thread it belongs to has broken the convention.

## Reading untagged messages

- No tag means `[meta]`: mechanism talk, housekeeping, one-off asks that open
  no thread.
- If an untagged message clearly continues an open thread, the agent answers
  under that thread's tag and says nothing about the choice unless it was
  close.
- If the agent itself opens a new thread (a task it started), it proposes the
  tag in `[meta]` (`I'll track this as [porch]`) and uses it from its next
  reply. The user's tags always win over the agent's.

## Renaming, closing, parking

- Rename: the user states it (`[hedge] is now [land]`); the agent updates the
  index and keeps the old word as an alias until the next session.
- Close: `[tag] done`. The agent marks the tag closed in the index (charter
  and final state stay readable) and stops prefixing with it.
- A thread with nothing in flight parks itself: no live back-and-forth, state
  in the index, resumed by the next `[tag]` mention in any session.

## The tag tree

Doctrine here, memory elsewhere: this file describes the mechanism and holds
no live data. Each agent owns a tag tree in its own durable store.

- Layout: `tags/index.md` plus one directory per tag, `tags/NNNN/`, holding
  `history.md`.
- `index.md` is the read model: one line per tag with its number, word,
  charter, current state, and status (live, parked, closed). It is the only
  mutable file; every question about a thread is answered from its line.
- `tags/NNNN/history.md` is the trail: dated, append-only entries, one file
  per tag, read whole when resuming. One file, not many: split a tag's
  history only when the single file stops being easy to read, and archive
  within the tag's own directory when that day comes.
- Allocation is by mkdir. The agent picks the next number, `mkdir tags/NNNN`.
  Success claims it, and the agent appends the tag's line to `index.md`.
  Failure means the number was taken in a race: back off (3s), increment the
  number, retry. Numbers, not words, name the directories so a rename edits
  the index and never the tree; the index maps each word to its number.
- Renames and closes edit the index only. History keeps everything.

## Hygiene

- Three or fewer threads live at once. Past that, park one.
- A tag labels; it never substitutes for content. The message still makes its
  own point.
- Don't re-teach the convention mid-thread. `[meta]` exists for that.
