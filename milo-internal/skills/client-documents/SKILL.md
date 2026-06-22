---
name: client-documents
description: >
  This skill should be used when the user wants to build a locked client-facing
  MILO deliverable: a Coaching Agreement or a Leader Install Roadmap. Triggers
  include "build a coaching agreement", "draft the coaching agreement for [client]",
  "create the leader install roadmap", "draft the install roadmap", or any request
  to produce one of these client documents to the approved template.
metadata:
  version: "0.2.0"
  source: "Locked document templates (approved May–June 2026)"
---

# Client Documents

Build locked, client-facing MILO deliverables to their approved templates. These are
sales-and-delivery artifacts you produce for a client, not something a client
generates. Two documents live here: the Coaching Agreement and the Leader Install
Roadmap. The full templates, formatting details, and the page naming convention are
in `references/document-templates.md`. Follow them exactly.

## Page naming convention (all client-facing documents)

- Format: `CLIENT NAME | DOCUMENT TYPE | DATE`
- All caps for the entire title.
- Pipe separators with a single space on both sides.
- Date format: `YYYY-MM-DD`.
- Name first gives a clean sort-by-client view. Document type in the middle
  identifies the deliverable. Date at the end anchors the version.
- Examples:
  - `BENN VAN RYN | MILO.TEAMS.OS SERVICE & BUILD AGREEMENT | 2026-06-04`
  - `LUKE FENN | MILO.TEAMS.OS LEADER INSTALL ROADMAP | 2026-06-05`
  - `JUSTIN BENNETT | MILO.LIFE.OS DIAGNOSTIC | 2026-05-15`
- Keep `™` out of titles. Titles are organisational labels, not legal surfaces.

## Voice

- Warm, conversational, second-person ("you"), no contractions, no em dashes, active voice.
- No banned words.
- Use the plain text `™` character in body text, never the emoji.

## Notion editing safety

- Never use a full replace-content operation on an existing page. Use targeted
  old_str / new_str edits, and fetch the current page state before editing.
- A brand-new empty page may be filled with one insert.

## What to build

When asked for a Coaching Agreement, follow the 7-section Coaching Agreement template.
When asked for a Leader Install Roadmap, follow the 3-phase Leader Install Roadmap
template. Both are specified in full in `references/document-templates.md`.
