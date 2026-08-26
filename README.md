# game-project-cartographer

A cartographer for mixed-material territories: bodies of work where truth is spread across code, content files, design docs, and external state. Drop this folder into a Claude project, point the AI at the territory, and it walks the work and leaves a map behind. The map is the product.

The later reader of that map is often a model — a cold session with no memory. Sometimes it is a new person. Same map. Same job.

## What to feed it

One territory root. A repo, a vault, a delivery folder — anything where a cold reader would get lost, and where code alone does not hold the whole truth. This cartographer was built against a live game project (Phaser code + ink narrative + JSON records + markdown design docs + an external task board). Its rules transfer to any territory of that shape.

Do not feed it a failure to explain or a methodology to describe. It maps things that are in force and will be changed.

## How a cold model walks

1. Read `identity.md`, then `rules.md`. That is the whole method.
2. Walk the territory following the procedure in `rules.md`. Consult `reference/card-types.md` when classifying, `reference/card-template.md` when writing.
3. Leave the map **in the territory**, as `map/` at the territory root: `catalog.md`, `collisions.md`, and a `cards/` folder. Optionally, a rendered `surface.html` — the human door (see below).
4. Archive the same run to `runs/YYYY-MM-DD/` inside this folder — the trail. The territory's `map/` is always the newest run. Keep the trail with the repo when the map is the deliverable (a submission). Git-ignore `runs/` when the territory's map must stay private.

Everything the map shows a reader is plain language and follows ASD-STE100 (see `rules.md`, "Write plain").

`examples.md` shows one worked map so you know what done looks like.

## The one rule for map readers

Load `map/catalog.md`, then open **one** card, then stop. Never load the whole `cards/` folder. The catalog points. The cards live on the shelves. If you find yourself loading everything, the map has failed you or you are failing the map.

## Two doors, one map

A model enters through `catalog.md`. A person enters through `surface.html`, a self-contained rendered view of the same map — the territory laid out spatially, with the chains a change lights up and the wrong doors marked. The surface is a pure projection of the cards: nothing on it that a card does not say. If the surface and a card disagree, the card wins. If a card and the real file disagree, the file wins. Both doors end at the same cards.

## What is in this folder

| File | Job |
|---|---|
| `identity.md` | Who the cartographer is and who reads the maps |
| `rules.md` | The walk, as a procedure, plus the refusals |
| `examples.md` | One worked map of a real territory, abridged |
| `reference/card-types.md` | The closed set of card types |
| `reference/card-template.md` | The card skeleton, copyable |
| `reference/collisions.md` | Naming collisions in the worked territory, and the rule that each territory gets a fresh list |
| `reference/surface-spec.md` | How to render the map's human door, `surface.html` |
| `runs/YYYY-MM-DD/` | The trail: one dated folder per run. Ships with the repo when the map is the deliverable; git-ignore it when the map must stay private. |
