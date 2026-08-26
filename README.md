# game-project-cartographer

A cartographer for mixed-material territory — a body of work where the truth is split across code, content files, design docs, and an outside task board. Drop this folder into a Claude project, point it at the territory, and it walks the whole thing and leaves a map behind. The map is the product.

The map's later reader is usually a model — a cold session with no memory of the work. Sometimes it is a new person. Same map. Same job.

## What to feed it

One territory root: a repo, a vault, a delivery folder. Anything where a cold reader would get lost, and where the code alone does not hold the whole truth.

I built this to map **my own game**, a real project I am making. It was caught mid-engine-pivot — two engines, an ink narrative pipeline, JSON content records, markdown design docs, and an outside task board. The map in `runs/` is that game. The rules transfer to any territory of the same shape.

Do not feed it a post-mortem or a method to write up. It maps what is live and will change.

## How a cold model walks

1. Read `identity.md`, then `rules.md`. That is the whole method.
2. Walk the territory by the procedure in `rules.md`. Use `reference/card-types.md` to classify a noun, `reference/card-template.md` to write its card.
3. Leave the map **in the territory**, as `map/` at its root: `catalog.md`, `collisions.md`, and a `cards/` folder. Add a rendered `surface.html` — the human door — if you want one (see below).
4. Archive the same run to `runs/YYYY-MM-DD/` in this folder. That is the trail. The territory's `map/` is always the newest run. Keep the trail in the repo when the map is the deliverable, like a submission. Git-ignore `runs/` when the territory's map must stay private.

Everything the map shows a reader is plain language and follows ASD-STE100 (see `rules.md`, "Write plain").

`examples.md` shows one worked map, so you know what done looks like.

## The one rule for map readers

Load `map/catalog.md`, open **one** card, then stop. Never load the whole `cards/` folder. The catalog points. The cards sit on the shelves. If you are loading everything, the map failed you or you are failing the map.

## Two doors, one map

The same map has two entrances.

### An agent enters here — `catalog.md`

A cold agent loads `catalog.md`, opens one card, and reads to the source. The catalog points. The cards sit on the shelves. It never loads the whole `cards/` folder.

### A human enters here — `surface.html`

A person opens `surface.html` — the same map, drawn as a chart. The territory is laid out in space, with the chain a change sets off lit up and the wrong turns marked. You walk it by hand: hover a mark to preview it, click a noun to travel to its card. When a task board is connected, each part also shows its open work as a dated snapshot.

### Both doors end at the same cards

The surface is a pure projection of the cards. Nothing is on it that a card does not say, except the open-work layer, which is marked as coming from the board. If the surface and a card disagree, the card wins. If a card and the real file disagree, the file wins.

## What is in this folder

| File | Job |
|---|---|
| `identity.md` | Who the cartographer is, and who reads the maps |
| `rules.md` | The walk, step by step, plus the refusals |
| `examples.md` | One worked map of a real territory, abridged |
| `reference/card-types.md` | The closed set of card types |
| `reference/card-template.md` | The card skeleton, copyable |
| `reference/collisions.md` | Naming collisions from the worked territory, plus the rule: each territory gets a fresh list |
| `reference/surface-spec.md` | What the human door, `surface.html`, must show |
| `reference/surface-template.html` | The human door as a working skeleton — the full engine plus example data. Fill the data blocks, do not rebuild the engine. |
| `runs/YYYY-MM-DD/` | The trail: one dated folder per run. Ships with the repo when the map is the deliverable. Git-ignore it when the map must stay private. |
