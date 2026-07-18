# tldraw (Obsidian Plugin)

**Pattern:** Rich Drawing
**Repo:** tldraw/obsidian-plugin
**Version:** v1.29.0
**Downloads:** ~430

## Why It Matters

Richest drawing surface available in Obsidian. Data stored as markdown — agents can read/write.

## Data Format

Markdown files with embedded JSON between delimiters:

```
---
tldraw-file:
  plugin-version: "1.29.0"
  uuid: "..."
---
!!!_START_OF_TLDRAW_DATA__DO_NOT_CHANGE_THIS_PHRASE_!!!
{serialized tldraw store JSON}
!!!_END_OF_TLDRAW_DATA__DO_NOT_CHANGE_THIS_PHRASE_!!!
```

Outside delimiters: regular markdown (backlinks, tags, properties).

## Agent I/O

Parse markdown → extract JSON between delimiters → modify → write back. More complex than JSON Canvas but richer drawing capabilities.

## Comparison to JSON Canvas

| Aspect | tldraw | JSON Canvas |
|--------|--------|-------------|
| Drawing primitives | Everything | Nodes + edges only |
| Agent I/O | Parse delimiters | Direct JSON |
| Vault integration | Backlinks in markdown | File nodes |
| Visual richness | High | Low |

## Status

Installed in Orenda WIP vault. Data format not yet tested for agent manipulation.

## Source

Leo, 2026-07-18. README analysis + source code inspection.
