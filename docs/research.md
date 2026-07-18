# Research Notes

## Existing Multiplayer Whiteboards

### tldraw
- https://github.com/tldraw/tldraw
- TypeScript, React, Canvas2D
- Multiplayer via Yjs (CRDT)
- Open source, MIT license
- Key reference: collaboration protocol, presence, undo/redo

### Excalidrop
- https://github.com/excalidraw/excalidraw
- TypeScript, React, Canvas2D
- Multiplayer via WebRTC + custom sync
- Open source, AGPL-3.0
- Key reference: drawing tools, scene serialization

### Miro
- Proprietary, commercial
- Infinite canvas, real-time collaboration
- Key reference: UX patterns, tool palette, collaboration UX

### FigJam
- Proprietary, Figma
- Real-time whiteboard
- Key reference: sticky notes, reactions, cursor presence

## Hermes Plugin Research

### Plugin API
- Desktop app plugins: UI panes + commands
- Gateway plugins: platform adapters
- Native MCP tools: external tool integration
- Reference: `hermes-desktop-plugins` skill

### Collaboration Options
1. **Yjs (CRDT)** — battle-tested, offline-first, multiple providers
2. **Automerge** — CRDT, Rust core, good for documents
3. **Custom OT** — simpler but requires central server
4. **WebRTC + CRDT** — peer-to-peer, no server needed

### Rendering Options
1. **SVG** — easy manipulation, good for diagrams, limited for freehand
2. **Canvas2D** — fast, good for drawing, harder to manipulate objects
3. **WebGL** — fastest, best for large scenes, complex to implement
4. **Hybrid** — Canvas2D for drawing, SVG/DOM for UI overlays

## Open Questions
- Is this a Hermes desktop plugin or a standalone web app?
- How does it integrate with agent sessions?
- Does each agent get its own canvas, or is it shared?
- What's the persistence model? (file-based, database, both?)
