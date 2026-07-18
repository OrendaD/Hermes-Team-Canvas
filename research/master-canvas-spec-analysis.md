# Master Canvas Spec — Analysis & Transferable Concepts

**Source:** Arts Bro, "Master Canvas: Product and Technical Specification for Third-Third-Party Evaluation and Implementation" v0.1, 18 July 2026
**Analyzed by:** Leo, 2026-07-18
**Status:** Research — not a design decision

## What This Is

A 2,800-line product specification for a **standalone desktop application** — not an Obsidian plugin. Electron + Rust/WASM/WebGPU + SQLite + content-addressed storage + WARC web capture. A multi-year, multi-person build targeting 100,000+ objects with GPU-rendered spatial canvas.

The spec is unusually mature. The domain model reflects deep thinking about asset identity, locators, collection semantics, and the distinction between visual and conceptual organisation. Worth studying regardless of whether we build the full product.

## Where It Overlaps With Our Work

| Concept | Master Canvas | Hermes Team Canvas | Transferable? |
|---------|--------------|-------------------|--------------|
| **One canonical project graph** | All assets, relationships, annotations belong to one graph. Views are projections. | Same principle — canvas nodes link to vault notes, one knowledge graph. | ✅ Core principle |
| **AI integration model** | Provider-independent, scope is explicit, source-traceable, suggested vs confirmed. | Same — agents produce content that's distinguishable from human-authored. | ✅ Direct transfer |
| **Collection vs Visual Frame** | Collection = semantic membership. Visual Frame = spatial container. Moving into Frame doesn't change membership. | We need this distinction — a node can be in a group on canvas without changing its vault relationships. | ✅ Critical concept |
| **Locators as first-class** | Precise source references (PDF page+rectangle, video time range, image region, webpage element) are first-class project objects. | Our canvas nodes need to link back to precise vault locations, not just files. | ✅ Direct transfer |
| **User correction layers** | Machine-generated content (OCR, transcripts, entities) stored separately from user edits. Reprocessing doesn't erase corrections. | Agents produce suggestions. Human confirms or edits. Corrections persist. | ✅ Direct transfer |
| **Machine vs human distinction** | AI-suggested links, entities, clusters MUST remain distinguishable from user-confirmed structure. | Same — agent nodes on canvas are visually distinct from human nodes. | ✅ Direct transfer |

## Where It Diverges

| Aspect | Master Canvas | Hermes Team Canvas | Why Different |
|--------|--------------|-------------------|--------------|
| **Application type** | Standalone Electron desktop app | Obsidian plugin | We extend Obsidian; he replaces it |
| **Rendering** | Rust/WASM/WebGPU, 64-bit world coords, LOD, spatial index | JSON Canvas or tldraw, Obsidian renders | Different performance envelope |
| **Storage** | SQLite + content-addressed filesystem + WARC | Obsidian vault (markdown files) | We use Obsidian's storage |
| **Scale target** | 100,000 objects, 10M+ words | Dozens to hundreds of nodes | Different complexity class |
| **Media handling** | PDF.js, FFmpeg, OCR, transcription, webpage capture | We don't handle media — we link to vault notes | Different scope |
| **Web preservation** | WARC/WACZ capture, isolated replay | Not in scope | Different scope |
| **Platform** | Cross-platform Electron | Obsidian (Electron-based) | Overlapping runtime, different architecture |

## Transferable Concepts

### 1. The Collection / Visual Frame Distinction

**Master Canvas definition:**
- **Collection:** Semantic membership. Many-to-many. "This note belongs to Chapter 3."
- **Visual Frame:** Spatial container. View-local. "This node is grouped here on this canvas."

Moving a node into a Visual Frame MUST NOT change its Collection membership unless the user explicitly requests it.

**For Hermes Team Canvas:** This is critical. When an agent places a node on the canvas and groups it with other nodes, that's a Visual Frame — a spatial arrangement. The node's vault relationships (which folder it's in, which other notes it links to, which collections it belongs to) are unaffected.

**Implementation:** Canvas groups in JSON Canvas are Visual Frames, not Collections. The vault's folder structure and wikilinks are Collections. The distinction is already built into the format — we just need to name it correctly in our design docs.

### 2. Locators as First-Class Objects

**Master Canvas definition:** A Locator identifies a precise position inside a source version. Types include PDF page+rectangle, video time range, image region, webpage element anchor, transcript segment, spreadsheet cell range.

**For Hermes Team Canvas:** When an agent creates a node on the canvas that links to a vault note, the link should be precise — not just "note X" but "note X, heading Y, block Z." When an agent references a finding from a dossier, the link should point to the exact passage.

**Implementation:** Obsidian's `[[note#heading]]` and `[[note#^block]]` syntax already supports this. We should use it consistently in agent-generated canvas content.

### 3. Suggested vs Confirmed

**Master Canvas definition:** AI-suggested links, entities, contradictions, clusters, summaries, and classifications MUST remain distinguishable from user-confirmed project structure.

**For Hermes Team Canvas:** Agent nodes on the canvas should be visually distinct from human nodes. Agent suggestions should be clearly marked. Human confirmation should upgrade an agent suggestion to a confirmed element.

**Implementation:** tldraw node types or JSON Canvas color coding. Agent-created nodes get a distinct color or border. Human-confirmed nodes get a different style.

### 4. One Canonical Graph, Multiple Views

**Master Canvas definition:** All assets belong to one canonical project graph. Views are projections — not independent sources of truth that must be synchronised.

**For Hermes Team Canvas:** The vault is the canonical graph. Canvas views are projections of vault relationships. Multiple canvases can show different views of the same vault content without duplicating or fragmenting it.

**Implementation:** Canvas files reference vault notes via `file` nodes. The vault is the source of truth. Canvas is a visual layer over it.

### 5. Degradation Must Be Explicit

**Master Canvas definition:** When a format, capture, relink, extraction, or replay is incomplete, the application MUST report the limitation. It MUST NOT silently pretend that a partial result is complete.

**For Hermes Team Canvas:** When an agent can't fully process a source (unsupported format, failed OCR, incomplete extraction), the canvas node should indicate the limitation. Don't silently show partial results as complete.

**Implementation:** Agent nodes carry status metadata. "Processed: partial — OCR failed on page 5." Visible in node properties.

## What We Should NOT Transfer

| Concept | Why Not |
|---------|---------|
| Rust/WASM/WebGPU renderer | Overkill for our scale. JSON Canvas + Obsidian rendering is sufficient. |
| SQLite + content-addressed storage | Obsidian's vault IS our storage. Don't replicate it. |
| WARC web capture | Out of scope. We link to vault notes, not capture webpages. |
| FFmpeg/OCR/transcription workers | Out of scope. We process text, not media. |
| 100,000-object benchmark | Our target is hundreds of nodes, not tens of thousands. |
| Electron standalone app | We're building an Obsidian plugin, not a new application. |

## Recommendation

1. **Adopt the domain vocabulary** — Collection, Visual Frame, Locator, Suggested vs Confirmed. These are precise terms that improve our design discussions.

2. **Adopt the AI integration model** — Provider-independent, source-traceable, suggested vs confirmed. This maps directly to our agent-canvas interaction model.

3. **Adopt the "one canonical graph" principle** — Vault is the source of truth. Canvas is a projection. This is already implicit in our design but should be stated explicitly.

4. **Do NOT adopt the rendering architecture** — Different scale, different runtime, different constraints.

5. **Do NOT adopt the storage architecture** — We use Obsidian's vault, not a custom SQLite + content-addressed filesystem.

6. **Add ADR-002** — "Adopt Master Canvas domain vocabulary for design discussions." This gives us shared language with the broader community.

## Related

- [Interaction Models](../architecture/interaction-patterns.md)
- [Canvas Formats](canvas-formats.md)
- [Plugin Landscape](plugin-landscape.md)
