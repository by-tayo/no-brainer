---
title: Active Work
aliases: [active, in flight, current]
type: dashboard
status: active
tags: [moc]
created: 2026-09-15
updated: 2026-09-15
summary: What is in flight right now, plus the inbox backlog and anything stale.
related: ["[[Home]]", "[[All Notes]]"]
---

# Active Work

```base
filters:
  and:
    - '!file.inFolder("95-Templates")'
    - '!file.inFolder("99-Archive")'
    - 'type != "moc"'
    - 'type != "dashboard"'
    - 'type != "daily"'
views:
  - type: table
    name: In flight
    filters:
      and:
        - 'status == "active"'
    order:
      - file.name
      - type
      - updated
      - summary
    sort:
      - property: updated
        direction: DESC
  - type: table
    name: Ideas and paused
    filters:
      or:
        - 'status == "idea"'
        - 'status == "paused"'
    order:
      - file.name
      - type
      - status
      - summary
  - type: table
    name: Inbox backlog
    filters:
      and:
        - 'file.inFolder("00-Inbox")'
    order:
      - file.name
      - created
```

## Daily log

Dailies are excluded from the views above on purpose — they would drown everything else. They live in `05-Daily`.

```base
filters:
  and:
    - 'file.inFolder("05-Daily")'
views:
  - type: table
    name: Recent dailies
    limit: 30
    order:
      - file.name
      - summary
    sort:
      - property: file.name
        direction: DESC
```

## Links

- Up: [[Home]]
- Related: [[All Notes]]
