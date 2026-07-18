# Canvas Branch Chat

**Pattern:** Node-as-Conversation (Primary)
**Repo:** p4nt1um/canvas-branch-chat
**Version:** v0.2.3
**Status:** Very new (1 week old)

## Why It Matters

Closest to Pattern 5 in the agent-canvas space. Branching creates spatial exploration, not just chat history.

## How It Works

- Each canvas node is a message (user question or AI response)
- Fork from any node with direction labels
- Context inheritance along ancestor chain
- Multi-model per branch (different perspectives)
- Token-level streaming to canvas nodes
- Export to markdown with hierarchy

## Agent-Canvas Relationship

Agent generates nodes but doesn't persist between interactions. However, the spatial arrangement of branches creates a thinking map — navigable thought terrain.

## Building Block for Pattern 5

Spatial conversation model + context inheritance + multi-model branching. Could be extended to persistent agent presence.

## Source

Sherlock research, 2026-07-14.
