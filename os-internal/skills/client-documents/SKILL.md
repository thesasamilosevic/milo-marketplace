---
name: client-documents
description: >
  This skill should be used when the user wants to build a locked client-facing
  MILO deliverable: a Coaching Agreement, a Leader Install Roadmap, or a
  MILO.CUSTOM.OS Build Log, or to run the post-call build analysis on a build log.
  Triggers include "build a coaching agreement", "draft the coaching agreement for
  [client]", "create the leader install roadmap", "draft the install roadmap",
  "build the build log for [client]", "create the client build log", "analyze the
  build call", "run the build analysis for [client]", or any request to produce
  one of these client documents to the approved template.
metadata:
  version: "0.4.0"
  source: "Locked document templates (approved May–July 2026)"
---

# Client Documents

Build locked, client-facing MILO deliverables to their approved templates. These are
sales-and-delivery artifacts you produce for a client, not something a client
generates. Three documents live here: the Coaching Agreement, the Leader Install
Roadmap, and the MILO.CUSTOM.OS Build Log, plus the build analysis flow that runs
after a build log call. The Coaching Agreement and Leader Install Roadmap
templates, formatting details, and the page naming convention are in
`references/document-templates.md`. The Build Log template is in
`references/build-log-template.md`. The build analysis flow is in
`references/build-analysis.md`. Follow them exactly.

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

## Sharing safety

- A client can duplicate any page shared with them, child pages included, into
  their own workspace. Master templates, internal notes, and unfinished system
  builds never sit on a client-shared page. Systems get built privately and only
  the finished page is copied into the client's OS.

## What to build

When asked for a Coaching Agreement, follow the 7-section Coaching Agreement template.
When asked for a Leader Install Roadmap, follow the 3-phase Leader Install Roadmap
template. Both are specified in full in `references/document-templates.md`.
When asked for a Build Log, follow the 2-section Build Log template in
`references/build-log-template.md`. Question titles must match the client's install
roadmap Phase 2 deliverable names exactly, and discovery questions are mined from
the Granola pitch and closing call transcripts.
When asked to analyze a build call or stage the build, follow
`references/build-analysis.md`: coverage map first, Saša approves, then the SYSTEM
PACKAGE callouts get their build specs.
When asked to build a roadmap from a client's form answers (the Closing Pipeline
C or T question columns), follow `references/roadmap-from-form.md` for sourcing
and mapping, and the locked roadmap template for the page itself.
