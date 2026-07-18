# ADR-002: Adopt Master Canvas Domain Vocabulary

## Status

**Proposed** — 2026-07-18

## Context

Arts Bro's Master Canvas specification (v0.1, 18 July 2026) defines precise terms for concepts our project also needs. Without shared vocabulary, design discussions about canvas grouping, source linking, agent contributions, and vault relationships become ambiguous.

The Master Canvas spec is a standalone desktop application spec (Electron + Rust/WASM/WebGPU). We are building an Obsidian plugin. The architectures diverge significantly. But the domain model — how assets, relationships, views, and AI contributions are conceptualised — is transferable.

## Decision

Adopt the following Master Canvas terms as canonical vocabulary for Hermes Team Canvas design discussions:

### Collection
A semantic membership structure. Many-to-many. "This note belongs to Chapter 3." In our context: vault folders, tags, wikilinks, and manual groupings.

### Visual Frame
A view-local spatial container. Moving an object into a Visual Frame does not change its Collection membership. In our context: canvas groups, node arrangements, spatial layout.

### Locator
A precise position or range inside a source. Types include text range, page+rectangle, time range, image region, block reference. In our context: `[[note#heading]]`, `[[note#^block]]`, and richer references for non-text sources.

### Suggested vs Confirmed (Confirmation Lifecycle)
AI-generated content (links, entities, clusters, summaries) is visually and structurally distinct from user-confirmed content. This is a lifecycle — suggestions are created by agents, then confirmed or rejected by humans — not a choice between two equal options. In our context: agent nodes on canvas are marked as suggestions until human confirms.

### One Canonical Graph
All assets belong to one canonical project graph. Views are projections, not independent sources of truth. In our context: the vault is the canonical graph. Canvas files are projections of vault relationships.

### Explicit Degradation
When processing is incomplete (failed OCR, unsupported format, partial extraction), the limitation is reported. Partial results are never silently shown as complete. In our context: agent nodes carry status metadata indicating processing completeness.

## Rationale

These terms resolve ambiguity in our existing design discussions:

- "Grouping" is ambiguous — is it semantic membership (Collection) or spatial arrangement (Visual Frame)? The distinction prevents confusion.
- "Linking" is ambiguous — is it a file reference or a precise source location? Locator gives us precision.
- "Agent content" is ambiguous — is it a suggestion or a confirmed element? Suggested vs Confirmed gives us a lifecycle.
- "Source of truth" is ambiguous — is it the canvas or the vault? One Canonical Graph makes the vault authoritative.

## Consequences

### Positive
- Shared vocabulary with the broader community (Arts Bro and collaborators)
- Precise terms for design discussions and ADRs
- Prevents ambiguity in canvas-vault relationship descriptions

### Negative
- Terms may be unfamiliar to new contributors (mitigated by CONTRIBUTING.md glossary)
- Master Canvas spec is v0.1 — terms may evolve (we adopt the concepts, not the spec version)

### Risks
- Vocabulary adoption implies conceptual alignment — we should note where we diverge (architecture, scale, rendering) to avoid false equivalence

## Related

- [Master Canvas Spec Analysis](../research/master-canvas-spec-analysis.md)
- [Interaction Models](../architecture/interaction-models.md)
- [Canvas Formats](../research/canvas-formats.md)
