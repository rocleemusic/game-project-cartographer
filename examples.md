# Worked example: the game-project map

The territory is a live game project in a private repo (`RL_MAP/ProjectOS/game-project/`): a Phaser 4 TypeScript build, an ink narrative compiled to `story.json`, JSON content records, 16 numbered design docs, a narrative pipeline, and an external task board (Paca). Mid-flight engine pivot (Unreal → Phaser, 2026-08-17), so the ground is layered: live systems sit next to a 624-file `-old` folder, frozen pipeline runs, and playtest debris.

The later reader is a model — the next cold Claude session working the repo. All paths below are real, relative to the territory root. This is an abridged copy; the full map lives in the territory at `map/`.

## The catalog (abridged)

| Noun | Status | Card |
|---|---|---|
| soul — a character; card of record in `cast/` | live | `cards/soul.md` |
| story.json — the compiled ink graph both hosts read | live | `cards/story-json.md` |
| run folder — resolver output, lantern input | live | `cards/run-folder.md` |
| cue — a spell VFX entry in the CueTable | live | `cards/cue.md` |
| seat contract — an agent's job description | live | `cards/seat-contract.md` |
| register — the prose voice rules for narrative output | live | `cards/register.md` |
| Paca board — external task state, GP-nnn ids | live | `cards/paca-board.md` |
| pipeline run — dated, frozen output of a narrative run | ghost | `cards/pipeline-run.md` |
| assignment-7-old — superseded assignment tree | leftover | `cards/assignment-7-old.md` |

## Card: soul

```markdown
---
name: soul
type: content-record
status: live
record: cast/
---

## What it is
A character in the game. One markdown card per soul in `cast/` (mara.md,
ilsa.md, juno.md, ...). The card is the canonical persona: voice, threads,
relationships. Ink content and generated records derive from it, which is
why it is a flat folder of small files — each pipeline run reads a few
souls, never the folder.

## Doors
- `cast/mara.md` — a representative card
- `narrative-pipeline/npc-codex.md` — how souls enter pipeline runs

## Hits
Changing a soul card hits future narrative-pipeline output and any ink
content written against it (`lantern-projects/v01/`). Rulings about a
soul made mid-session must flow back to `cast/`, or the next run works
from a stale persona.

## Does not hit
`pipeline-runs/*/` contain copies of soul cards with the same filenames.
They are frozen run inputs and knowingly diverge from `cast/`. Editing
one changes nothing live. Reading one as canon imports last month's
persona. The card in `cast/` is the soul; everything else is a photograph.
```

## Card: cue

```markdown
---
name: cue
type: code-system
status: live
record: phaser/src/render/vfx/CueTable.ts
---

## What it is
A spell VFX entry: which spritesheet plays, at what frame rate, anchored
where. The table exists because VFX are data-tuned, not code-tuned —
calibration happens by editing numbers, and the backend
(`phaser/src/render/vfx/PhaserVfxBackend.ts`) just plays what the table
says.

## Doors
- `phaser/src/render/vfx/CueTable.ts` — the table itself
- `PAUSED.md` — the calibration rulings, per cue

## Hits
Changing a cue's `originY` moves where the effect sits on its anchor.
Trap, from PAUSED.md: the `leap` cue's `originY: 0.6667` is tied to a
torch/ring vertical offset baked into its composited texture. Do not
recompute it from measurement. Changing that offset means rebuilding
the sheet, not editing the number.

## Does not hit
`phaser/src/magic/` — the obvious word to reach for ("it's a spell"),
but magic/ is the casting mechanics, not the visuals. A cue change never
touches spell logic, costs, or targeting.
```

## Card: pipeline run (a ghost)

```markdown
---
name: pipeline-run
type: run-artifact
status: ghost
record: pipeline-runs/
---

## What it is
A dated, frozen snapshot of one narrative-pipeline run
(`pipeline-runs/2026-07-25-kinbound/`, ...). Kept as evidence of what a
run saw and produced. Frozen on purpose: it must show what the run
actually used, so it is never updated when canon moves.

## Hits
Nothing. That is the point of the card.

## Does not hit
Everything a cold reader thinks it hits. These folders contain soul
cards, prompts, and outputs with live-looking names. None of it is
wired. The live versions are `cast/` and `narrative-pipeline/`.
```

## One change, traced

**Change: retune the `ignite` cue's anchor.**

Walk: catalog → `cards/cue.md` → `phaser/src/render/vfx/CueTable.ts`.

The card says: edit the table entry, check PAUSED.md for that cue's calibration ruling (ignite's `originY: 0.371` was "wrong twice before landing" — re-measure, don't eyeball). Hits: the rendered effect and the PAUSED.md ruling table, which must be updated to match. Does not hit: `phaser/src/magic/`, and not the `leap` cue's rule — leap's originY is texture-baked, ignite's is measured. Two cues, same field, different physics of change. That distinction is the map earning its keep.

Reader stops. Total load: catalog + one card + one source file.
