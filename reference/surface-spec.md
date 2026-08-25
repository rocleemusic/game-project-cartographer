# Surface spec — the human door

Optional step 7 of the walk: after the map passes the honesty checks, render `map/surface.html` — one self-contained HTML file, no server, no external assets, no framework.

What the page shows, and nothing else:

1. **Header** — territory name, walk date, the authority note, and the walk printed as a rule: catalog → one card → source → stop.
2. **Intents** — the 4-6 changes a reader actually brings ("change a mechanic", "change the content"), as toggles. Selecting one lights its chain across the seam and dims everything else. Intent labels are change verbs, never workflow stages.
3. **The seam chart** — two shore columns from the catalog's Shore marks, off-shore nouns below, one chip per noun with its status lamp. Edges drawn between chips: solid for wired hops, dashed for manual hops a human carries. Wrong doors on a lit chain render dashed-red.
4. **Per-noun detail** — clicking a chip shows only that card's Hits and Does-not-hit plus its record path, and ends with the door: "full card at cards/x.md — open it, then the source, then stop." Never the full card body.
5. **Collisions** — every entry, one line each, warn styling. Collisions are the one section a skimmer should absorb whole.
6. **Scoped-out and footer** — silence shown as decision, plus the authority chain: surface loses to card, card loses to file.

Rules:

- **Pure projection.** Every word comes from catalog.md, collisions.md, or a card. Nothing invented, nothing dropped that a reader would call load-bearing. Edges only exist where a Hits line states them.
- **A door, not a destination.** The page hands the reader to a card; it never replaces one.
- **Honest edges.** Manual hops look different from wired hops. Open questions and stated dead ends appear as text, not as missing pixels.
- Quality floor: responsive to mobile, visible keyboard focus, reduced motion respected, works from `file://`.
