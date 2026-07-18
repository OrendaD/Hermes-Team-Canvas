# Hermes Team Canvas

Multiplayer infinite multimedia whiteboard for Hermes.

## What Is This

A Hermes plugin that adds a collaborative whiteboard to agent sessions.
Agents and humans draw, annotate, and iterate on visual ideas together
in real time — architecture diagrams, mind maps, flowcharts, sketches.

## Status

Background research phase. No code yet.

## Architecture (Draft)

```
hermes-team-canvas/
├── plugin/           # Hermes plugin entry point
│   ├── __init__.py
│   └── plugin.py
├── server/           # WebSocket collaboration server
├── canvas/           # Canvas engine (rendering, tools, state)
├── frontend/         # UI layer (HTML/JS, Hermes desktop integration)
├── docs/             # Research, references, decisions
└── scripts/          # Dev tooling
```

## Research Needed

- [ ] Hermes plugin API surface (hooks, commands, desktop integration)
- [ ] Collaboration protocols (CRDT vs OT vs custom)
- [ ] Canvas rendering options (SVG, Canvas2D, WebGL)
- [ ] State sync architecture
- [ ] Existing multiplayer whiteboard references (tldraw, Excalidrop, etc.)

## License

MIT
