# Obsidian Markdown — Locator Syntax

**Source:** kepano/obsidian-skills/skills/obsidian-markdown
**Date:** 2026-07-18
**Status:** Research

## What It Is

Obsidian Flavored Markdown extends CommonMark with wikilinks, embeds, callouts, properties, and other syntax. This note covers the locator-relevant extensions — how to link precisely to content within notes.

## Precise Locators

### Heading Links
```markdown
[[Note Name#Heading]]              Link to a heading
[[#Heading in same note]]          Same-note heading link
```

### Block Links
```markdown
[[Note Name#^block-id]]            Link to a specific block
```

Define a block ID by appending `^block-id` to any paragraph:
```markdown
This paragraph can be linked to. ^my-block-id
```

For lists and quotes, place the block ID on a separate line:
```markdown
> A quote block
^quote-id
```

### Embeds (Precise)
```markdown
![[Note Name]]                     Embed full note
![[Note Name#Heading]]             Embed a section
![[image.png]]                     Embed image
![[image.png|300]]                 Embed with width
![[document.pdf#page=3]]           Embed PDF page
```

### Display Text
```markdown
[[Note Name|Display Text]]         Custom display text
```

## Agent Application

**Every agent-generated canvas link should use precise locators.** Not just `[[Note]]` but:

- `[[Note#Heading]]` — links to a specific section
- `[[Note#^block-id]]` — links to a specific paragraph or block
- `![[Note#Heading]]` — embeds a specific section in a canvas text node

**For canvas nodes linking to dossiers:**
```markdown
![[dossier-name#Key Findings]]
```

**For canvas nodes linking to specific passages:**
```markdown
[[dossier-name#^specific-evidence-block]]
```

## Other Obsidian Syntax (Agent-Relevant)

### Comments (Hidden Metadata)
```markdown
%%This is hidden in reading view%%
```

Agent can embed status, processing metadata, or provenance in comments that humans don't see in reading view but agents can read.

### Callouts (Structured Content)
```markdown
> [!note] Title
> Content here
```

Agent-generated canvas text nodes can use callouts for structured information — warnings, summaries, questions.

### Properties (Frontmatter)
```yaml
---
title: My Note
date: 2024-01-15
tags:
  - project
  - active
---
```

Canvas nodes with `file` type inherit the note's frontmatter. Agent-generated notes should include relevant properties.

## Related

- [Obsidian CLI](obsidian-cli.md)
- [Canvas Formats](canvas-formats.md)
