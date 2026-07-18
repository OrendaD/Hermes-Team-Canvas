# Architecture — Hermes Team Canvas

## Vision

A multiplayer infinite whiteboard where Hermes agents are first-class citizens — spatial, visible, interactive participants alongside humans on the same canvas surface.

## Design Principles

1. **Agents on canvas, not in sidebar.** The whiteboard is the collaboration surface. Agents live on it, not behind it.

2. **JSON-native, file-based.** Canvas state is files on disk. Agents read/write files. No proprietary APIs, no binary blobs, no server dependencies.

3. **Layout is delegated.** Agents describe intent — nodes, edges, relationships. Layout algorithms determine spatial arrangement. Agents never compute coordinates.

4. **Vault-integrated.** Canvas nodes link to vault notes. Canvas is part of the knowledge graph, not separate from it.

5. **Graceful degradation.** Core canvas operations work without plugins. Advanced features (events API, presentation mode) enhance but don't gate.

## Current Design Artifacts

| Document | Status |
|----------|--------|
| [Interaction Models](interaction-models.md) | ✅ Complete |
| [Data Flow](data-flow.md) | 🔲 Not started |
| [Plugin Design](plugin-design.md) | 🔲 Not started |

## Diagrams

Architecture diagrams live in `diagrams/` as Mermaid source files. Render to SVG for embedding in markdown.
