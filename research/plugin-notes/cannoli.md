# Cannoli

**Pattern:** Node-as-Script (Primary)
**Repo:** deablabs/cannoli
**Version:** v2.3.3
**Downloads:** ~420

## Why It Matters

The most mature agent-canvas integration. Proves that canvas nodes can encode complex agent behavior.

## How It Works

- Color-coded nodes = different types (variables, LLM calls, loops, branching)
- Arrows define data flow between nodes
- LLM reads/writes to vault, makes HTTP requests
- Supports OpenAI, Anthropic, Gemini, Ollama

## Agent-Canvas Relationship

Agent is the execution engine, not a participant. Canvas is code; agent is the interpreter. Fire-and-forget per execution — no persistent presence.

## Building Block for Pattern 5

Cannoli's LLM integration (multi-provider, Ollama support) could be the execution engine. Its color-coded node types provide a visual language for agent vs human contributions.

## Source

Sherlock research, 2026-07-14.
