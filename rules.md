# Rules

The walk, in order. Do not write cards until step 4. Do not write the catalog until the cards exist.

## 1. Inventory before cards

Walk the territory root. List candidate nouns before describing any of them.

A **noun** is a thing the territory operates on or with: a system, a record type, a document of record, a contract, an artifact format, an external store. A noun earns a card when a change to it could ripple somewhere non-obvious, or when a cold reader would plausibly grab the wrong version of it. Folders are not automatically nouns. Files are not automatically nouns. "The build output" can be a noun. "src/" is usually several.

A **movement** is how a noun changes or flows: what produces it, what consumes it, what regenerates it. Movements live on cards, not as cards.

Target 8–15 cards for a territory a person works in daily. If you have 30, you are photocopying. If you have 3, check the ghosts — undercounting usually means you skipped the confusing parts.

## 2. Find the file of record

For every noun, name the one path that wins when sources disagree. In mixed territory the same noun often appears in several places — a canonical card, a frozen copy in a run artifact, a deployed copy, a test fixture. Exactly one is the record. The card names it in frontmatter. If you cannot decide which copy is the record, that is a finding — write it on the card, do not guess silently.

## 3. Classify: live, leftover, ghost

- **Live** — changed recently, wired in, someone will change it again. Check churn (git log, modified dates), not the name on the folder.
- **Leftover** — superseded but honest: an `-old` folder, an archive, a build artifact. It says what it is. Mark it so the reader spends zero attention on it.
- **Ghost** — a name with no wiring: a frozen copy that diverged from its record, a scratch area that looks like the source, debris that accumulated. Ghosts are tripwires. They get marked because a cold reader **will** reach for them.
- **Dormant** — parked, not superseded and not dead: a track deferred past a milestone, a branch waiting on a decision. Mark it dormant and name what would wake it. Do not force it into leftover — leftover means superseded, and dormant things come back.

A name on a file is not a live object. Mapping a wish as live is how the next reader implements the wrong world.

## 4. Hunt the prose for couplings

Import statements and file references will not give you the real edges. Before writing Hits lines, read the territory's own memory: PAUSED files, CONTEXT files, index rulings, register docs, contract audits. You are hunting for sentences shaped like "do not recompute this", "X restates Y", "this is tied to". Those are the edges the map exists to carry. Cite where you found each one.

## 5. Write the cards

Use `reference/card-template.md`. Every card carries:

- **Hits** — if you change this, what moves. Paths, not vibes.
- **Does not hit** — the obvious next noun that is the wrong one. Name it and say why it is wrong. Without this line you wrote a glossary.

Cards cite. They do not copy. If a card contains a block of the source, delete the block and point at it. Two to four sentences of "what it is and why it is shaped that way" is the ceiling.

## 6. Catalog last

One line per noun plus a door (the card path). The catalog stores almost nothing — it points. Then the reader's walk is: catalog → one card → the cited source → stop.

## Refusals

- Refuse to inline source into cards. Point instead.
- Refuse a "load everything" README. The one rule is catalog, then one card.
- Refuse to map the wish. If a doc describes a system that is not wired, the card says ghost, whatever the doc claims.
- Refuse to rank, fix, or diagnose. If asked "so what should I change first?", answer: that is not the map's job — here is the card for the thing you are changing.

## Honesty checks (run before calling the map done)

1. **No dead doors.** Every path cited on every card exists in the territory right now. Check each one.
2. **No orphaned live systems.** Every subsystem that shows recent churn is claimed by some card, or the catalog says explicitly why it is out of scope. Silent omission reads as "covered" when it is not.
