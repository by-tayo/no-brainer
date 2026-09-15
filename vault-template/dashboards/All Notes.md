---
title: All Notes
aliases: [all notes, everything, note index]
type: dashboard
status: active
tags: [moc]
created: 2026-09-15
updated: 2026-09-15
summary: Every note in the vault as a filterable, editable table. Built with Bases, not Dataview.
related: ["[[Home]]", "[[Vault Conventions]]"]
---

# All Notes

Cells here are editable — changing `status` in this table rewrites the note's frontmatter.

```base
filters:
  and:
    - '!file.inFolder("95-Templates")'
    - '!file.inFolder("99-Archive")'
views:
  - type: table
    name: Everything
    order:
      - file.name
      - type
      - status
      - updated
      - summary
    sort:
      - property: updated
        direction: DESC
  - type: table
    name: By section
    order:
      - file.name
      - type
      - status
      - file.folder
    sort:
      - property: file.folder
        direction: ASC
  - type: table
    name: Needs a summary
    filters:
      and:
        - 'summary == ""'
    order:
      - file.name
      - type
      - updated
```

## Links

- Up: [[Home]]
- Related: [[Active Work]], [[Vault Conventions]]
