# Worked example: the game-project map

The territory is a live game project in a private repo (`RL_MAP/ProjectOS/game-project/`): a Phaser 4 TypeScript build, an ink narrative compiled to `story.json`, JSON content records, 17 numbered design docs, a narrative pipeline, and an external task board (Paca). Mid-flight engine pivot (Unreal → Phaser, 2026-08-17), so the ground is layered: live systems sit next to a 624-file `-old` folder, frozen pipeline runs, and playtest debris.

The later reader is a model — the next cold Claude session working the repo. All paths below are real, relative to the territory root. This map was produced by a cold agent that read only this cartographer folder and the territory. What follows is abridged; the full map (21 cards plus a 12-entry collision list) lives in the territory at `map/`.

## The catalog (abridged)

The real catalog opens with the authority note ("Highest-authority prose: `CONTEXT.md` at the territory root — read it before anything") and a pointer to `map/collisions.md`. Then 21 nouns. A sample:

| Noun | Status | Card |
|---|---|---|
| soul — a character; card of record in `cast/` | live | `cards/soul.md` |
| run folder v01 — the playable week, home of `story.json` | live | `cards/run-folder-v01.md` |
| cue — a spell's VFX entry, data-driven | live | `cards/cue.md` |
| phaser build — the ship target since the 2026-08-17 pivot | live | `cards/phaser-build.md` |
| register — the voice contract for player-facing text | live | `cards/register.md` |
| Paca board — external task state, `GP-nnn` ids | live | `cards/paca-board.md` |
| pipeline run — dated run output; only the newest is pending intake | live | `cards/pipeline-run.md` |
| Unreal port — parked post-capstone; wakes after 2026-09-01 ships | dormant | `cards/unreal-port.md` |
| assignment-7-old — superseded tree with duplicate interior names | leftover | `cards/assignment-7-old.md` |

It closes with a "Scoped out, on purpose" section — e.g. `phaser/src` interior detail is claimed by one card whose doors point at the territory's own `ARCHITECTURE.md`, because card-per-subfolder would photocopy that doc.

## Card: soul

```markdown
---
name: soul
type: content-record
status: live
record: cast/
---

## What it is
A character in the game. One markdown card per soul in `cast/` (`mara.md`,
`toby.md`, `ilsa.md`, ...), each the canonical persona: voice, threads,
relationships. Deep souls also carry a `-threads.md` file beside the card —
a companion, not a second card. Flat small files because a pipeline run
reads a few souls, never the folder.

## Doors
- `cast/mara.md` — a representative card
- `narrative-pipeline/templates/persona-card-schema.md` — the shape a card must hold
- `narrative-pipeline/npc-codex.md` — how souls enter pipeline runs

## Hits
Changing a soul card hits future narrative-pipeline output and dialogue
generated against it. Rulings about a soul made mid-session must flow back
to `cast/` or the next run works from a stale persona (`CONTEXT.md` §Where
things live: "This is the card of record — the pipeline-runs copies are
frozen run artifacts and diverge. Edit here").

## Does not hit
`pipeline-runs/*/` copies of soul cards — frozen run inputs, knowingly
divergent. Also `gdd/07-cast.md`: it holds the roster design, not any one
soul's persona. Roster-shape changes go there; persona changes go to `cast/`.
```

## Card: cue

```markdown
---
name: cue
type: code-system
status: live
record: phaser/src/render/vfx/cues.json
---

## What it is
A spell VFX entry: kind (none/filter/particles/tint/glow/sprite),
spritesheet, frame rate, anchor. Entries live in data (`cues.json`), not
code, because VFX are tuned by editing numbers — `PhaserVfxBackend.ts`
plays what the data says, `CueTable.ts` holds the types and shared formulas.

## Doors
- `phaser/src/render/vfx/cues.json` — the entries
- `PAUSED.md` (territory root) — per-cue calibration rulings

## Hits
Changing a cue's kind hits the no-effect-honesty parity check: `tint` and
`sprite` use different weight formulas, so neutrals can flip. Trap from
PAUSED.md: `leap`'s `originY: 0.6667` is tied to a torch/ring offset baked
into its composited texture — do not recompute it from measurement;
changing the offset means rebuilding the sheet. `ignite`'s `originY: 0.371`
is the opposite physics: measured, re-measure it.

## Does not hit
`phaser/src/magic/` — the obvious word ("it's a spell"), but that is
casting mechanics. A cue change never touches spell logic. And not
`content/magic/*.json` — the spell record decides outcomes, the cue only
decides what the outcome looks like.
```

Note the record: `cues.json`, a data file. An earlier draft of this example named the TypeScript table as the record. The cold walk corrected it — calibration had moved into the data, and the file wins over the card.

## Card: pipeline run (aging instances)

```markdown
---
name: pipeline-run
type: run-artifact
status: live
record: pipeline-runs/
---

## What it is
A dated snapshot of one narrative-pipeline run. Older runs are frozen
evidence — never updated when canon moves, so a cold reader treats their
contents as photographs. Status is live because the newest run
(`2026-08-25-full-content-generation/`) is fresh, unconsumed raw material.

## Hits
Only the newest run hits anything, and only via the polish pass that folds
approved text into the dialogue inventory and ink. Once folded, that folder
joins the frozen ones and hits nothing.

## Does not hit
`cast/` and `narrative-pipeline/` — the live originals. Run folders contain
soul cards, prompts and outputs with live-looking names; none of it is
wired, and editing a copy changes nothing.
```

This is the status-aging rule in action: one noun, instances that freeze on landing, status set by the newest.

## One change, traced

**Change: retune the `ignite` cue's anchor.**

Walk: catalog → `cards/cue.md` → `phaser/src/render/vfx/cues.json`.

The card says: edit the entry, check PAUSED.md for that cue's calibration ruling (ignite's `originY: 0.371` was "wrong twice before landing" — re-measure, don't eyeball). Hits: the rendered effect and the ruling table, which must be updated to match. Does not hit: `phaser/src/magic/`, and not the `leap` cue's rule — leap's originY is texture-baked, ignite's is measured. Two cues, same field, different physics of change. That distinction is the map earning its keep.

Reader stops. Total load: catalog + one card + one source file.
