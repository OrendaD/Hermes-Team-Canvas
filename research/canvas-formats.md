# Canvas Formats

Three canvas/whiteboard formats relevant to Hermes Team Canvas.

## JSON Canvas

**Spec:** [jsoncanvas.org/spec/1.0](https://jsoncanvas.org/spec/1.0/)
**Maintainer:** Obsidian team
**Status:** Open standard, v1.0 (March 2024)

Pure JSON. Nodes (text/file/link/group) + edges. Coordinate-based positioning. Clean agent I/O.

| Pros | Cons |
|------|------|
| Pure JSON — agent reads/writes with standard file tools | Nodes + edges only — no freehand drawing |
| Typed nodes (text, file, link, group) | Coordinate burden without layout engine |
| Edges with directional semantics | Single-writer (no concurrent edits) |
| Vault-integrated (file nodes link to notes) | No event stream for agent reactivity |
| Official skill from kepano/obsidian-skills | Limited visual richness |

**Agent I/O:** Direct JSON read/write. Best for structured content (diagrams, knowledge graphs, kanban).

## tldraw

**Repo:** [tldraw/obsidian-plugin](https://github.com/tldraw/obsidian-plugin)
**Maintainer:** tldraw + community
**Status:** Active, v1.29.0

Rich drawing surface. Shapes, freehand, text, arrows, images, everything. Data stored as markdown with embedded JSON between delimiters.

| Pros | Cons |
|------|------|
| Rich drawing primitives — not just nodes+edges | Delimiter-based parsing (fragile?) |
| Markdown files — vault-integrated | JSON blob between delimiters is opaque |
| Freehand, shapes, images, text | Agent must parse/modify delimiters |
| Community plugin, actively maintained | More complex than JSON Canvas |
| Interactive canvas in browser | Data format is tldraw-specific |

**Agent I/O:** Parse markdown, extract JSON between delimiters, modify, write back. More complex but richer.

## Excalidraw

**Repo:** [zsviczian/obsidian-excalidraw-plugin](https://github.com/zsviczian/obsidian-excalidraw-plugin)
**Maintainer:** Community
**Status:** Mature, large user base

Hand-drawn style diagrams. Similar to tldraw but focused on diagramming. Data stored as JSON in markdown.

| Pros | Cons |
|------|------|
| Hand-drawn aesthetic — popular for docs | Less rich than tldraw |
| Markdown storage | Excalidraw-specific format |
| Large community, well-tested | Diagramming focus, not freeform |

**Agent I/O:** Similar to tldraw — JSON in markdown. Good for diagrams, less for freeform.

## Comparison

| | JSON Canvas | tldraw | Excalidraw |
|---|---|---|---|
| **Drawing primitives** | Nodes + edges | Everything | Diagram-focused |
| **Data format** | Pure JSON | Markdown + JSON delimiters | Markdown + JSON |
| **Agent I/O** | Direct | Parse delimiters | Parse delimiters |
| **Vault integration** | File nodes | Backlinks in markdown | Backlinks in markdown |
| **Visual richness** | Low | High | Medium |
| **Layout burden** | Agent must compute | Interactive | Interactive |
| **Community** | Obsidian standard | Growing | Mature |

## Recommendation

**JSON Canvas for structured agent output.** Clean I/O, no parsing fragility. Best for diagrams, knowledge graphs, pipeline visualizations.

**tldraw for rich interactive whiteboarding.** When humans need freeform drawing alongside agent content.

**Excalidraw for diagramming.** When the hand-drawn aesthetic is desired.

Not mutually exclusive — a Hermes canvas plugin could support multiple formats. Start with JSON Canvas (simplest), add tldraw support later.
