---
title: Vault Conventions
aliases: [conventions, schema, vault schema]
type: reference
status: reference
tags: [ctx/reference, kind/notes]
created: 2026-09-15
updated: 2026-09-15
summary: The property schema, tag vocabulary, and naming rules every note in this vault follows.
related: ["[[Home]]"]
---

# Vault Conventions

Read this first — it is the contract the whole vault (and any AI reading it) depends on.

## Folders

| Folder | Holds |
|---|---|
| `00-Inbox` | Unsorted captures. Empty it, do not let it become an archive. |
| `01-MOCs` | Maps of Content — the navigation layer. |
| `05-Daily` | Daily notes, `YYYY-MM-DD`. Excluded from the Active Work views. |
| `10-Classwork` | One note per course. |
| `20-Competitions` | One note per event, grouped by org (e.g. `NCL/`). |
| `30-Internships` | One note per role. |
| `40-Projects` | One note per project, or a folder per project if it grows. |
| `50-Reference` | Cheat sheets, command references, things you look up. |
| `90-Assets` | Images and attachments. |
| `95-Templates` | Note templates. |
| `99-Archive` | Dead but not deletable. |

The four content sections are numbered so they stay in alphabetical order: Classwork, Competitions, Internships, Projects.

## Properties

Every note carries these. Names and types never vary — Bases and Graph both depend on that.

| Property | Type | Values |
|---|---|---|
| `title` | text | Matches the filename. |
| `aliases` | list | Other names this note should resolve under. |
| `type` | text | `course`, `competition`, `internship`, `project`, `reference`, `moc`, `daily` |
| `status` | text | `idea`, `active`, `paused`, `complete`, `reference` |
| `tags` | list | From the vocabulary below only. |
| `created` | date | ISO `YYYY-MM-DD`, never changes. |
| `updated` | date | ISO `YYYY-MM-DD`, bump on every real edit. |
| `summary` | text | One line. This is what makes the vault scannable. |
| `related` | list | Wikilinks to sibling notes. |

Type-specific extras: `course-code`, `term`, `institution` (course) · `org`, `event`, `start-date`, `end-date`, `placement` (competition) · `org`, `role`, `start-date`, `end-date` (internship) · `repo`, `stack` (project).

`status` means one thing only — progress. There is no second maturity axis on purpose.

## Tag vocabulary

Controlled. Do not invent new ones without adding them here first.

- **Context** — `ctx/classwork`, `ctx/competition`, `ctx/internship`, `ctx/project`, `ctx/reference`
- **Kind** — `kind/notes`, `kind/writeup`, `kind/lab`, `kind/cheatsheet`, `kind/decision`, `kind/retro`
- **Domain** — `sec/blue`, `sec/red`, `sec/crypto`, `sec/cloud`, `sec/network`, `sec/appsec`, `sec/grc`
- **Structural** — `moc`

No `#` in frontmatter tags.

## Naming and linking

- Note filenames are Title Case with spaces: `Byte Lotus.md`, not `byte-lotus.md`.
- Never use `# | ^ : %` or `[ ]` in a filename — they break wikilinks.
- Link with wikilinks (`[[Note]]`), never relative paths. Links resolve by filename, so a note can move folders freely.
- Rename notes **inside Obsidian** (F2) so backlinks update. Renaming from the file explorer or a shell breaks every inbound link.
- Every new note gets linked from at least one MOC before you close it. That is the rule that keeps the graph connected.

## Links

- Up: [[Reference MOC]]
- Related: [[Home]]
