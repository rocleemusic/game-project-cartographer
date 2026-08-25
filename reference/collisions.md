# Naming collisions

Chat is not always Chat. In mixed territory the same name lands on several different things, and the collisions are where cold readers get hurt. This file lists the collisions in the worked territory (the game project). **Each new territory gets its own list, built fresh during step 1 of the walk, written to `collisions.md` beside the map's catalog.** Do not carry these entries to another map — carry the habit.

## The worked territory's collisions

**story.json is five files.** `lantern-projects/v01/story.json` is the source of record. `lantern-projects/scratch/story.json` is a scratch copy. `phaser/public/story/story.json` is the deployed copy the Phaser build serves. `phaser/dist/story/story.json` is build output. `tools/lantern/fixtures/story.json` is a test fixture. Edit the wrong one and the change either vanishes on the next build or breaks a test that was passing honestly.

**A soul card is not always the soul.** `cast/mara.md` is the record. `pipeline-runs/*/` hold same-named copies, frozen and knowingly divergent. `cast/mara-herbalist-threads.md` is a threads file beside the card, not a second card.

**assignment-7 is not assignment-7-old.** `assignments/assignment-7/` is live. `assignments/assignment-7-old/` is 624 superseded files with the same interior names. Search results mix them freely — check the path segment before trusting any hit under `assignments/`.

**"style guide" is three documents.** `assignments/assignment-7/style-guide.md` is a derived restatement of `narrative-pipeline/register.md` (the record for prose voice). `gdd/14-visual-style-guide.md` governs visuals and has a live rendered counterpart at `phaser/tools/screen-flow/mockups/design-system.html`. Prose questions go to register.md. Visual questions go to the GDD pair. The assignment copy is never the source.

**"spell" splits into cue and magic.** The visual half is a cue (`phaser/src/render/vfx/CueTable.ts`). The mechanical half lives in `phaser/src/magic/`. The word "spell" appears in both and wires to neither's neighbor.

**Tasks live in two worlds.** The Paca board (external, GP-nnn ids) holds current task state. Markdown in the repo holds reasoning and history. An archived backlog exists under `resources/_archive/` and is superseded — a task found only there is not a task.

**The test command is not one command.** `tools/resolver` tests run under `node --test`. `tools/lantern` tests run under `vitest`. Running the wrong runner in the wrong folder fails in ways that look like broken code.

## Writing a collision entry

One bolded claim naming the collision, then the resolution: which path is the record, what the other holders are, and the one-line consequence of grabbing the wrong one. If a collision has no resolution yet, say so — an honest open collision beats a guessed winner.
