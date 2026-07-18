# Interaction Models

Six patterns for how agents relate to canvas surfaces. The framework for design decisions.

## The Patterns

### Pattern 1: Sidebar Chat
Agent lives in a sidebar panel. Canvas is read-only context. Agent can reference notes but doesn't touch the canvas surface.

**Examples:** Hermes Agent plugin, Claude Code integration, most agent plugins
**Status:** Overcrowded (7/10 plugins)

### Pattern 2: Node-as-Script
Each canvas node is a script/LLM call. Arrows define data flow. Agent is the execution engine, not a participant.

**Example:** Cannoli
**Status:** Mature but niche (1 plugin)

### Pattern 3: Node-as-Conversation
Each canvas node is a message in a thread. Canvas visualises conversation history. Agent generates nodes but doesn't "live" on the canvas.

**Examples:** Canvas Branch Chat, Chat Stream, Spider
**Status:** Growing (2-3 plugins)

### Pattern 4: Event-Driven Agent
Agent responds to canvas events (node created, moved, modified). Reactive, not persistent.

**Example:** Advanced Canvas events API (potential, not yet realised by any agent plugin)
**Status:** Biggest gap — API exists but nobody uses it

### Pattern 5: Spatial Agent Presence
Agent has a persistent node or zone on the canvas. Can be triggered by human actions, modifies canvas autonomously, visible as a participant.

**Examples:** None
**Status:** Empty. This is our target.

### Pattern 6: Knowledge Graph Agent
Agent builds/maintains a graph structure on canvas. Nodes are entities, edges are relationships. Agent is the graph engine.

**Examples:** Vault Intelligence (Graph RAG), Spider (knowledge map)
**Status:** Emerging but conceptual — none express the graph visually on canvas

## Pattern Matrix

See [Interaction Pattern Matrix](../research/interaction-pattern-matrix.md) for the full 10-plugin classification.

## What Pattern 5 Needs

Composing building blocks from existing plugins:

1. **Trigger mechanism** → Advanced Canvas events API
2. **Execution engine** → Cannoli's LLM integration or Hermes gateway
3. **Spatial model** → Canvas Branch Chat's branching + Spider's auto-layout
4. **Persistence** → Vault Operator's three-layer memory
5. **Approval workflow** → Vault Operator's "every write needs approval"
6. **Visual language** → Cannoli's color-coded nodes + Canvas Branch Chat's distinction

No single plugin provides all six. The building blocks exist but haven't been composed.

## Related

- [Interaction Pattern Matrix](../research/interaction-pattern-matrix.md)
- [Plugin Landscape](../research/plugin-landscape.md)
- [Canvas Formats](../research/canvas-formats.md)
