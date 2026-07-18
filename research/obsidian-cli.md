# Obsidian CLI — Programmatic Access

**Source:** kepano/obsidian-skills/skills/obsidian-cli
**Date:** 2026-07-18
**Status:** Research

## What It Is

An official CLI that interacts with a running Obsidian instance. Requires Obsidian to be open. Commands target the most recently focused vault by default, or a specific vault via `vault=<name>`.

## Key Commands

### Note Operations
```bash
obsidian read file="My Note"
obsidian create name="New Note" content="# Hello" template="Template" silent
obsidian append file="My Note" content="New line"
obsidian search query="search term" limit=10
```

### Properties and Metadata
```bash
obsidian property:set name="status" value="done" file="My Note"
obsidian backlinks file="My Note"
obsidian tags sort=count counts
```

### Daily Notes
```bash
obsidian daily:read
obsidian daily:append content="- [ ] New task"
obsidian tasks daily todo
```

### JavaScript Execution
```bash
obsidian eval code="app.vault.getFiles().length"
```

### Plugin Development
```bash
obsidian plugin:reload id=my-plugin
obsidian dev:errors
obsidian dev:screenshot path=screenshot.png
obsidian dev:dom selector=".workspace-leaf" text
obsidian dev:console level=error
```

## Agent Relevance

**Proof-of-concept without a plugin.** The `eval` command runs JavaScript in Obsidian's app context. An agent could:
1. Create a canvas file via `obsidian create name="research.canvas" content="..."`
2. Or use `obsidian eval` to manipulate canvas data through the plugin API
3. Search for notes via `obsidian search` and place them on canvas
4. Set properties on notes via `obsidian property:set`

**This means we can test agent→canvas I/O from the command line** before building a plugin. The CLI is the integration layer for initial prototyping.

## Limitations

- Requires Obsidian to be open
- Targets most recently focused vault by default (use `vault=` to target specific)
- `eval` runs in the app context — limited to what the Obsidian API exposes
- No direct canvas manipulation commands (create note, set property — yes. create canvas node, draw edge — not yet)

## Related

- [Canvas Formats](canvas-formats.md)
- [JSON Canvas Spec](json-canvas-spec.md) (in Leo's workspace)
