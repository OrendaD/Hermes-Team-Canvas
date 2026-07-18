# Obsidian Bases

Structured data format for Obsidian notes. `.base` files are YAML-driven queries over vault content.

## What It Does

Filter, sort, group, and display notes as tables, cards, or lists. Compute derived properties with formulas. Embed views in markdown notes.

## Structure

```yaml
filters:          # Which notes appear
formulas:         # Computed properties
properties:       # Display config
views:            # Table, cards, list, map
```

## Why It Matters for Hermes Canvas

- **Dossier queries** — filter dossiers by silo, bundle, source_type, date
- **Entity management** — query entities by mentions, links, tags
- **Dashboards** — table views of recent ingestions, bundle coverage
- **Canvas embedding** — `![[MyBase.base]]` in canvas text nodes

## Limitations

- YAML-based, not JSON — agents need YAML writers
- No real-time updates (file-based)
- Limited to Obsidian's property system

## Source

kepano/obsidian-skills, Obsidian help docs. Leo, 2026-07-18.
