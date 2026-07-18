# Canvas Test Journal

**Project:** Hermes Team Canvas
**Started:** 2026-07-18
**Purpose:** Track proof-of-concept tests, problems, and resolutions for agent→canvas I/O

---

## Test 1: External Canvas File Creation

**Date:** 2026-07-18
**Goal:** Verify that a JSON Canvas file written externally renders correctly in Obsidian.

**Setup:**
- Wrote `test-agent-canvas.canvas` to Orenda WIP vault using `write_file`
- Three nodes: text (markdown), file (vault note), text (locator)
- Two edges with labels

**Results:**
- ✅ Canvas file renders in Obsidian
- ✅ Text node renders markdown (bold, line breaks, headers)
- ✅ Edges draw with labels ("tests", "references")
- ❌ File node path wrong — `raw/papers/findings.md` doesn't exist in Orenda WIP
- ⚠️ Locator `[[raw/papers/findings#^block-id]]` rendered as plain text (note didn't exist)

**Resolution:**
- Fixed file node path to `Mastering Mermaid Diagrams.md` (exists in vault root)
- Changed locator to heading-level: `[[Mastering Mermaid Diagrams#What Is Mermaid?]]`

**Key Finding:** Agent can write JSON Canvas files externally. Obsidian renders them. The I/O loop works.

---

## Test 2: Correct File Path + Heading Locator

**Date:** 2026-07-18
**Goal:** Verify file node renders a preview, heading locator resolves.

**Setup:**
- Updated canvas with correct file path
- Locator changed to `[[Mastering Mermaid Diagrams#What Is Mermaid?]]`

**Results:** Pending — waiting for user to verify in Obsidian.

---

## Problems Log

| # | Problem | Resolution | Status |
|---|---------|-----------|--------|
| 1 | `obsidian` CLI not installed | Fell back to direct `write_file` | ✅ Resolved |
| 2 | File node path wrong | Corrected to existing note in vault | ✅ Resolved |
| 3 | Locator rendered as plain text | Changed to heading-level, needs note to exist | ⏳ Testing |

## Key Learnings

1. **JSON Canvas is agent-writable.** No special tools needed — just write valid JSON to a `.canvas` file.
2. **File nodes require exact vault-relative paths.** No extension needed, but path must resolve.
3. **Locators need the target note to exist.** Wikilinks to non-existent notes render as plain text.
4. **Text nodes render markdown.** Bold, headers, line breaks all work.
5. **Edges draw with labels.** Both directional and labelled edges work.

## Next Steps

- Test block-level locators (`[[Note#^block-id]]`)
- Test read-back: can we parse the canvas JSON after Obsidian renders it?
- Test modify-and-write: change a node, write back, verify change renders
- Test agent-generated content at scale (multiple nodes, complex graph)
