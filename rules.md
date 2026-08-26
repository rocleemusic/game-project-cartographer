# Rules

The walk, in order. Do not write cards until step 4. Do not write the catalog until the cards exist.

## 1. Inventory before cards

Walk the territory root. List candidate nouns before describing any of them.

A **noun** is a thing the territory operates on or with: a system, a record type, a document of record, a contract, an artifact format, an external store. A noun earns a card when a change to it could ripple somewhere non-obvious, or when a cold reader would plausibly grab the wrong version of it. Folders are not automatically nouns. Files are not automatically nouns. "The build output" can be a noun. "src/" is usually several.

A **movement** is how a noun changes or flows: what produces it, what consumes it, what regenerates it. Movements live on cards, not as cards.

While inventorying, **name the territory's major seam** — the boundary most changes must cross (design/build, source/deploy, authored/generated) — and place each noun on a shore. Some nouns sit on neither shore. The seam is where a map earns its keep: changes that stay on one shore are usually obvious, and changes that cross are where readers get lost.

Target 8–20 cards for a territory a person works in daily. If you have 30, you are photocopying. If you have 3, check the ghosts — undercounting usually means you skipped the confusing parts. Never merge two nouns whose Hits lines differ. A merged card that has to say "changing this half hits X, that half hits Y" is two cards.

## 2. Find the file of record

For every noun, name the one path that wins when sources disagree. In mixed territory the same noun often appears in several places — a canonical card, a frozen copy in a run artifact, a deployed copy, a test fixture. Exactly one is the record. The card names it in frontmatter. If you cannot decide which copy is the record, that is a finding — write it on the card, do not guess silently.

## 3. Classify: live, leftover, ghost

- **Live** — changed recently, wired in, someone will change it again. Check churn (git log, modified dates), not the name on the folder.
- **Leftover** — superseded but honest: an `-old` folder, an archive, a build artifact. It says what it is. Mark it so the reader spends zero attention on it.
- **Ghost** — a name with no wiring: a frozen copy that diverged from its record, a scratch area that looks like the source, debris that accumulated. Ghosts are tripwires. They get marked because a cold reader **will** reach for them.
- **Dormant** — parked, not superseded and not dead: a track deferred past a milestone, a branch waiting on a decision. Mark it dormant and name what would wake it. Do not force it into leftover — leftover means superseded, and dormant things come back.

When a noun has many instances that age at different rates — dated runs, handoffs, snapshots — status describes the newest instance, and the card says how instances age ("each run freezes on landing; only the newest is ever consumed"). Do not split one noun into a live card and a ghost card over aging alone.

A name on a file is not a live object. Mapping a wish as live is how the next reader implements the wrong world.

## 4. Hunt the prose for couplings

Import statements and file references will not give you the real edges. Before writing Hits lines, read the territory's own memory: PAUSED files, CONTEXT files, index rulings, register docs, contract audits. You are hunting for sentences shaped like "do not recompute this", "X restates Y", "this is tied to". Those are the edges the map exists to carry. Cite where you found each one.

One case to expect: **a deprecated container holding canon contents.** A handoff file the territory has declared retired can still carry live, load-bearing rulings. The container's status does not decide the contents' status. Cite the ruling from the card it governs, and record the container in the collisions list so nobody either trusts the whole file or discards the ruling with it.

## 5. Write the cards

Use `reference/card-template.md`. Every card carries:

- **Hits** — if you change this, what moves. Paths, not vibes. When a hit lands on something another card owns, name the target by its card noun — a bare destination ("this folds into ink") is a dangling edge nobody can follow. If the true answer is "the effect is out of reach" (shipped text no process re-touches), say that; an honest dead end beats a missing line.
- **Does not hit** — the obvious next noun that is the wrong one. Name it and say why it is wrong. Without this line you wrote a glossary.

Watch the direction of your caution. "Don't touch that" lines come easily. "Here is what you will touch" lines are the ones readers need and walkers under-write. Every live card should state its forward hits, not just its fences.

Cards cite. They do not copy. If a card contains a block of the source, delete the block and point at it. Two to four sentences of "what it is and why it is shaped that way" is the ceiling.

## 6. Catalog last

One line per noun plus a door (the card path). The catalog stores almost nothing — it points. Then the reader's walk is: catalog → one card → the cited source → stop.

The catalog carries two fixed extras, and nothing else:

- **An authority note in the header** — one or two lines naming the territory's highest-authority prose (its CONTEXT file, its front door) and the walk date. The front door is not a noun and gets no card. This is its official slot.
- **A pointer to the map's collision list.** The collision list is its own file, `collisions.md`, beside the catalog — not inside it. A map is three things: `catalog.md`, `collisions.md`, `cards/`.

## Write plain

Every word the map shows a reader — cards, catalog, collisions, and the surface — is plain language and follows ASD-STE100 (Simplified Technical English).

- One idea per sentence. Keep sentences short. Split a sentence that runs long.
- Active voice. Name the actor. Write "prep:content re-syncs the build", not "the build is re-synced".
- Use a simple word where one exists. Keep the territory's real names exact — a file path, an id, or a coined term is never simplified.
- One instruction per sentence. A step that does two things is two sentences.
- Cut a sentence that only repeats the one before it.

Plain does not mean vague. Full accuracy, plainer words. A path is still a path. A ruling is still a ruling.

## Runs leave a trail

Every run is dated and kept. Write the run's full output to `runs/YYYY-MM-DD/` inside this folder: catalog, collisions, cards, and the surface. A past run is never overwritten. That folder is the trail.

Keep the trail with the repo when the map is the deliverable — a submission, where the copies are the proof. Git-ignore `runs/` when the territory's map must stay private. That is the same rule that keeps map copies out of a public repo.

The live map, delivered to the territory's `map/`, is always the newest run. The territory holds one current snapshot. The cartographer folder holds the history.

The trail is what a later "what changed" view reads. It compares the newest run's `catalog.md` against the run before it. That view needs no task board and no git log — the two dated catalogs hold the difference.

## Refusals

- Refuse to inline source into cards. Point instead.
- Refuse a "load everything" README. The one rule is catalog, then one card.
- Refuse to map the wish. If a doc describes a system that is not wired, the card says ghost, whatever the doc claims.
- Refuse to rank, fix, or diagnose. If asked "so what should I change first?", answer: that is not the map's job — here is the card for the thing you are changing.

## Honesty checks (run before calling the map done)

1. **No dead doors.** Every path cited on every card exists in the territory right now. Check each one.
2. **No orphaned live systems.** Every subsystem that shows recent churn is claimed by some card, or the catalog says explicitly why it is out of scope. Silent omission reads as "covered" when it is not.
3. **The seam is crossed.** Take the changes a reader will actually bring (change a mechanic, change the content, change the look) and trace each across the seam through stated Hits edges, card to card, to where it lands. A chain that dead-ends on one shore means missing edges, not a quiet territory. A card pointing at a noun no card owns means a card is missing or a Hits line is vague.
