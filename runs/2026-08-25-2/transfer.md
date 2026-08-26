# What changed — run 2026-08-25 (run 1) → run 2026-08-25-2

A per-run diff of the **territory**, not the task board. It compares this run's
`catalog.md`, `collisions.md`, and cards against the run before it. Task-state change
lives in `open-work.md`.

The file snapshot moved forward between runs: late-night work (Paca updates to
03:05Z) landed a new pipeline run and a new phaser feature. This is real drift, not a
re-render.

## Nouns
- No nouns added, removed, or renamed. Still 23 cards.

## Records / doors that moved
- **pipeline run** — newest run is now `2026-08-25-thread-driven-scenes/`, not
  `2026-08-25-full-content-generation/`. The new run superseded the older run's
  dialogue output and settled the "Claude authors structure, local models write lines"
  split. The older run's item and key-item descriptions were still ingested into live
  canon (GP-207); its `content/magic/` descriptions stay pending.
- **dialogue inventory** — Phase 0 of the new run edited `gdd/15`: texture souls went
  from 1 to 2 greeting rows each (first-meeting + generic).
- **item record** — count corrected 17 → 16 common item records. Descriptions rewritten
  into field-notes voice and ingested (GP-207). New coupling: an item id now also names
  its art PNG at `phaser/public/art/items/${id}.png` (GP-208).
- **gdd-sync** — the spec is now an in-territory copy at `commands/gdd-sync.md` (record
  path changed from the out-of-territory `../../commands/gdd-sync.md`). The copy's paths
  point at the `ProjectOS/game-project/` source layout, not this repo.
- **session handoff** — newest handoff is
  `2026-08-25-thread-driven-scenes-run-handoff.md`; count 38 → 40.

## Collisions
- Added: two 2026-08-25 pipeline runs (newer retired older's dialogue);
  `lantern-projects/v01/threads/` is a retired format still on disk;
  `commands/gdd-sync.md` is a copy of a foreign command.
- Rewritten: the debris list — `.gitignore` now excludes the regenerable outputs, so the
  run-1 debris paths (`dist/`, `out-calib/`, `.playtest/`, `.adversary/`,
  `*.stackdump`) are absent from this public copy. Only
  `tools/resolver/P:tmpresolver_test_out.txt` remains.

## Routes / reach
- No route (Hits edge) added or removed. The item-art coupling rides inside
  item-record and phaser-build, which are already joined. Reach is unchanged.

## Open work
- 35 open → 33 open. GP-202, GP-203, GP-204 (T13/T14 phaser work) left the open set;
  GP-208 (item art) was added. Phaser build 18 → 16. See `open-work.md`.
