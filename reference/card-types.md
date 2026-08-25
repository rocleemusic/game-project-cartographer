# Card types

The closed set. A card's `type:` must be one of these six. Adding a type means editing this file — if you feel the pull to invent one mid-walk, you are probably describing a movement (which lives on a card) or a folder (which is usually several nouns).

| type | What it is | Record usually lives in |
|---|---|---|
| `code-system` | A subsystem the code operates: a table, an engine layer, a mode | source files |
| `content-record` | A record the work is made of: a character, an item, a scene | content/data files, one per record |
| `design-doc` | A document that governs shape or voice: a style guide, a register, a GDD section | markdown |
| `contract` | An agreement between parties: an agent seat, a schema, a folder-as-interface | markdown or schema files |
| `run-artifact` | Output of a run: a build, a dated pipeline snapshot, a report folder | generated folders |
| `external-state` | Truth held outside the territory's files: a task board, a sheet, a service | elsewhere — the card names the pointer |

Two rules that ride along:

- **Status is orthogonal to type.** A `run-artifact` can be live (today's build) or ghost (last month's frozen run). Classify by wiring and churn, not by type.
- **`external-state` cards carry the boundary.** Say what the files hold (reasoning, history) versus what the external store holds (current state), and which one wins for which question.
