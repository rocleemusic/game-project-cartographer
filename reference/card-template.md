# Card template

Copy this skeleton for every card. Every section is required except Doors on a ghost card (a ghost may have no doors worth opening).

```markdown
---
name: <noun, kebab-case>
type: <one of the six in card-types.md>
status: live | leftover | ghost
record: <the path that wins when sources disagree>
---

## What it is
Two to four sentences. What the noun is, and why it is shaped this way —
the reason for the shape is what a glossary lacks. No source pasted in.

## Doors
Two or three paths to go deeper, each with one line on what is behind it.

## Hits
If you change this, what moves. Concrete paths. Include any coupling you
found in the territory's prose (rulings, PAUSED files) and cite where.

## Does not hit
The wrong neighbor: the noun a cold reader will reach for, named, with
one line on why it is the wrong one.
```

Limits:

- A card is under 40 lines. Longer means you are photocopying — cut the copy, keep the pointer.
- `record:` is one path. If you had to list two, you have two nouns or an unresolved collision. Say which, on the card.
- If the card and the file at `record:` disagree, the file wins and the card is wrong. Fix the card.
