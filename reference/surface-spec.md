# Surface spec — the human door

Optional step 7 of the walk. After the map passes the honesty checks, render `map/surface.html`. One self-contained HTML file. No server, no framework, no external assets. Web fonts from Google Fonts are the one exception, and every face has a system fallback.

The surface is a **chart of the territory**, not a list. Design-side nouns sit on the left. Build-side nouns sit on the right. The seam runs between them as a channel. Off-to-the-side nouns run along the lower margin. A change travels left to right, toward what ships.

## What the page shows

1. **Title block** — territory name, walk date, the authority note, and one line on what the page is for (pick a change or a noun to see what it would affect). The walk itself — open one card, then the source, then stop — is stated at the door: the footer and each card's closing line. If a task board was read, this block also holds the open-work snapshot stamp and a "Do next" list (see "Open-work layer").
2. **Intents** — the 4–6 changes a reader actually brings ("a game mechanic", "the voice"), as toggles under "I want to change…". Pick one and its route lights across the seam. Everything else dims. The route also prints below as numbered steps, each tagged "carries itself" or "by hand". Intent labels are change verbs, never workflow stages.
3. **The chart** — one circle per noun, placed by shore. Circle size = reach (how much moves when you touch it). A small number by each circle counts the routes running through it. Edges join the circles: a solid line carries the change on its own, a dashed red line means a person carries it by hand. The chart zooms (scroll or buttons) and pans (drag). Hovering a circle shows a quick line — the noun, its side, status, route count, and role. Hovering an open-work dot lists the open tasks on that noun.
4. **Per-noun detail** — click a circle and a card opens in place below the chart. It shows that noun's Hits, its Does-not-hit, its record path, its open tasks (if a board was read), and the door line: "full card at cards/x.md — open it, then the source, then stop." Never the full card body. The chart does not scroll away on click. A down arrow in the chart's lower-right jumps the reader to the card. Closing the card resets the chart, and the close button says so. **The card is traversable:** the nouns it carries to and is fed by are links. Click one and that noun's card opens in its place, so a reader walks the map card to card without returning to the chart.
5. **Collisions** — every entry, one line each, warn styling. A skimmer should absorb this section whole.
6. **Scoped-out and footer** — silence shown as a decision, plus the authority chain: surface loses to card, card loses to file.

## The two marks a reader must not confuse

The chart uses red for two different things. Keep them distinct in shape and explain both in the legend.

- **Dashed red ring around a noun = the wrong turn.** It appears only when a change is picked. It marks the name a reader will reach for that does not do the work.
- **Filled dot on a noun = open work.** It shows the count of open tasks on that noun. Its colour is the hottest status among them.

A dashed hollow ring and a filled dot never read as the same mark.

## Open-work layer (only when the territory has a task board)

The map records structure, not task state. Task state lives on the board. This layer is the one place the two meet, and it is a **point-in-time snapshot**, not a live feed.

- Read the board once, when the page is made. Take the open work only — skip the backlog and anything done.
- File each open task to the **one noun where its change lands**. One task, one home, so the counts stay honest.
- Show it three ways: a snapshot stamp in the title block, a "Do next" list of the top few (rank by tier, then by what is in motion), and a per-noun count and task list in each detail card. A "Do next" row highlights its noun on hover and, on click, jumps to the chart with that noun selected.
- **Stamp the date.** Say plainly that the counts were read when the page was made, and point the reader to the live board.
- **Also write it as `map/open-work.md`.** The same snapshot, in markdown, beside the catalog: the counts, the "Do next" list, and the open work grouped by noun. The catalog points to it. The surface shows the snapshot; this file records it.
- **Fallback.** If the board cannot be reached on a run, hide the counts and show a short "not reached — reconnect and re-run" note. Never show a stale list as if it were current. Never invent task state.

The open-work layer answers "what work is open". It does not replace the board, and it is not the same as the transfer surface below.

## Transfer surface — what changed since the last run (optional, needs a trail)

A per-run page that reports how the **territory itself** changed, not how the work changed. It reads the trail (`runs/`), not the task board.

- Compare the newest run's `catalog.md` against the run before it.
- Report: nouns added, removed, or renamed; routes added or removed; status flips (live → leftover, dormant → live); and the shift in each noun's reach.
- A run with no earlier run to compare against has nothing to show. Skip the page until a second run exists.

This is a different axis from the open-work layer. A run can show zero task change and still have the map drift — a file moves, a noun splits, a route flips to by-hand. The board cannot see that. The two dated catalogs can.

## Rules

- **Pure projection.** Every word comes from `catalog.md`, `collisions.md`, or a card. The one exception is the open-work layer, which comes from the task board and is stamped as such. Nothing else is invented. Nothing load-bearing is dropped. Edges exist only where a Hits line states them.
- **A door, not a destination.** The page hands the reader to a card. It never replaces one.
- **Walkable, not just readable.** The reader moves through the map by hand — hover a mark to preview it, click a noun to travel to its card. Every noun the page names is a place you can go.
- **Honest edges.** A by-hand hop looks different from one that carries itself. Open questions and stated dead ends appear as text, not as missing pixels.
- **Write plain.** Every label and sentence follows the "Write plain" rule in `rules.md` (plain language, ASD-STE100).
- **Quality floor.** Responsive to mobile, visible keyboard focus, reduced motion respected, works from `file://`.
