# Status

**Last updated:** 2026-07-18

## Research Phase

| Area | Status | Owner |
|------|--------|-------|
| Canvas format analysis (JSON Canvas, tldraw) | ✅ Complete | Leo, Sherlock |
| Interaction pattern framework | ✅ Complete | Leo |
| Plugin landscape survey (10 plugins) | ✅ Complete | Sherlock |
| Interaction pattern matrix (10 plugins classified) | ✅ Complete | Sherlock |
| Obsidian Bases format analysis | ✅ Complete | Leo |
| kepano/obsidian-skills evaluation | ✅ Complete | Leo |
| Layout algorithm research | ✅ Complete | Leo |
| tldraw plugin deep-dive | ✅ Complete | Leo |
| Advanced Canvas events API investigation | 🔲 Not started | — |
| Hermes Agent plugin integration analysis | 🔲 Not started | — |
| Pattern 5 (Spatial Agent Presence) proof-of-concept | 🔲 Not started | — |

## Design Phase

| Area | Status | Owner |
|------|--------|-------|
| Architecture overview | 🔲 Not started | — |
| Plugin design (Hermes ↔ Canvas bridge) | 🔲 Not started | — |
| ADR-001: Canvas format decision | 🔲 Not started | — |
| ADR-002: Agent interaction model | 🔲 Not started | — |
| ADR-003: Layout engine approach | 🔲 Not started | — |

## Implementation Phase

| Area | Status | Owner |
|------|--------|-------|
| Hermes plugin scaffold | 🔲 Not started | — |
| JSON Canvas write from agent | 🔲 Not started | — |
| Advanced Canvas events integration | 🔲 Not started | — |
| Agent node type | 🔲 Not started | — |
| Layout algorithm integration | 🔲 Not started | — |

## Key Open Questions

1. **Canvas format:** JSON Canvas (clean I/O) vs tldraw (rich drawing) vs hybrid?
2. **Agent presence model:** How does an agent "live" on the canvas?
3. **Event bridge:** Advanced Canvas events API — what does it actually expose?
4. **Layout engine:** Where does coordinate computation happen — plugin, skill, or external script?
