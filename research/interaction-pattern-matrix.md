# Interaction Pattern Matrix

The classification framework for agent-canvas interaction. 6 patterns, 10 plugins mapped.

## Pattern Definitions

| # | Pattern | Description |
|---|---------|-------------|
| 1 | **Sidebar Chat** | Agent in sidebar, canvas is read-only context |
| 2 | **Node-as-Script** | Canvas nodes = LLM calls/scripts, arrows = data flow |
| 3 | **Node-as-Conversation** | Canvas nodes = messages in a thread, conversation visualized |
| 4 | **Event-Driven** | Agent responds to canvas events (node created/moved/modified) |
| 5 | **Spatial Presence** | Agent has persistent node/zone on canvas, modifies autonomously |
| 6 | **Knowledge Graph** | Agent builds/maintains graph structure on canvas |

## Matrix

| Plugin | Downloads | P1 Sidebar | P2 Script | P3 Conv | P4 Event | P5 Spatial | P6 KG |
|--------|-----------|:---:|:---:|:---:|:---:|:---:|:---:|
| Agent Client | 210K | ✅ | | | | | |
| AI Agent | 8.9K | ✅ | | | | | |
| Vault Operator | 7.8K | ✅ | | | ◐ | | ◐ |
| Claudian | 1.4K | ✅ | ◐ | | | | |
| Hermes Agent | 2.6K | ✅ | | | | | |
| Enzyme | 3.4K | ✅ | | | | | ◐ |
| Cannoli | 420 | | ✅ | | ◐ | | |
| Canvas Branch Chat | new | | | ✅ | | ◐ | |
| Spider | 1 | | | ✅ | | | ◐ |
| Vault Intelligence | 54 | | | | ◐ | | ✅ |
| Advanced Canvas | 1.4K | | | | ✅ | | |

**Legend:** ✅ = primary pattern, ◐ = secondary/emerging, blank = not present

## Gap Analysis

### Crowded
- **Sidebar Chat:** 7 of 10 plugins. Default. We don't need another.

### Underoccupied
- **Node-as-Script:** Only Cannoli. Mature but niche.
- **Event-Driven:** Only Advanced Canvas has the API. No agent plugin uses it. **Biggest gap.**
- **Knowledge Graph:** 3 plugins but all conceptual — none express the graph visually on canvas.

### Empty
- **Spatial Agent Presence:** Zero plugins. **This is our target.**

## Building Blocks for Pattern 5

| Component | Source | Status |
|-----------|--------|--------|
| Trigger mechanism | Advanced Canvas events API | Exists, unused |
| Execution engine | Cannoli LLM integration | Exists, composable |
| Spatial model | Canvas Branch Chat branching + Spider auto-layout | Exists, partial |
| Persistence | Vault Operator three-layer memory | Exists, vault-native |
| Approval workflow | Vault Operator "every write needs approval" | Exists, proven |
| Visual language | Cannoli color-coding + Canvas Branch Chat distinction | Exists, composable |

**No single plugin provides all six. Building blocks exist but haven't been composed.**

## Source

Research by Sherlock, 2026-07-14. Plugin data from GitHub repos and Obsidian community plugins.
