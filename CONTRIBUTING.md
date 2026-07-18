# Contributing to Hermes Team Canvas

Welcome! This repo is where we design the Hermes whiteboard. Everyone's research and ideas are welcome.

## Where Things Go

| You have... | Put it in... |
|-------------|-------------|
| A design proposal | `adr/` (use the ADR template) |
| Research about an external tool | `research/plugin-notes/<tool-name>.md` |
| An architecture decision | `architecture/` |
| A diagram | `architecture/diagrams/` (Mermaid `.mmd` files) |
| A question or discussion | [GitHub Discussions](https://github.com/OrendaD/Hermes-Team-Canvas/discussions) |

## Conventions

### Files
- Use lowercase with hyphens: `interaction-patterns.md`, not `Interaction Patterns.md`
- One idea per file in `research/` — keep files focused
- Mermaid diagrams: `.mmd` extension, rendered to SVG via `npx @mermaid-js/mermaid-cli`

### ADRs
- Number sequentially: `0001-`, `0002-`, etc.
- Use the template in `adr/template.md`
- Status: `proposed` → `accepted` → `deprecated`/`superseded`
- One decision per ADR

### Research
- Include the source URL and date
- Note what's opinion vs fact
- Link to related files with relative paths

### Diagrams
- Mermaid source in `.mmd` files
- Rendered SVGs committed alongside sources
- Use `flowchart TD` for architecture diagrams (portrait-friendly)
- Use `sequenceDiagram` for interaction flows

## Getting Started

1. Fork the repo
2. Read the [Architecture README](architecture/README.md) for context
3. Check [STATUS.md](STATUS.md) for what's in progress
4. Pick an open item or propose something new via an ADR
5. Submit a PR

## Code of Conduct

Be kind. Be constructive. Pushback on ideas, not people. Same as any Hermes fleet collaboration.
