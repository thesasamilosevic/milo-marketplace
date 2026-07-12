# Install Roadmap From the Closing Pipeline Form (approved July 2026)

How to generate a client's install roadmap from their Closing Pipeline form answers
instead of call transcripts. The output follows the locked Leader Install Roadmap
template in `references/document-templates.md`. This file covers where the source
data lives and how to turn answers into the page.

## Source data

The client's row in the Closing Pipeline database
(`collection://29c73928-9e3a-80d4-b920-000b8015de78`) holds the form answers as
page properties. The column prefix tells you which offering the answers serve:

- `C1` through `C7`: MILO.CUSTOM.OS questions (time drain, disorganization cost,
  tools and systems, team and role, 90-day vision, prior attempts).
- `T1` through `T7`: MILO.TEAMS.OS questions (team size, team structure and roles,
  tools and where work falls through, project intake and breakdown, capacity and
  scheduling, visibility up and down, 90-day team vision).
- `L/C/T8` and `L/C/T9`: shared questions (systems switch appetite, Notion
  familiarity). Read these for every roadmap.

Fetch the row and read every filled column for the matching prefix. Some answers
carry embedded red `Q U E S T I O N S` spans that Saša added while reviewing. Treat
those as open threads to weave into the roadmap or carry to the call. Never invent
an answer for an empty column.

## Which template and branding

- TEAMS.OS roadmap title: `CLIENT NAME | MILO.TEAMS.OS LEADER INSTALL ROADMAP | YYYY-MM-DD`.
- CUSTOM.OS roadmap title: `CLIENT NAME | MILO.CUSTOM.OS INSTALL ROADMAP | YYYY-MM-DD`.
- Page icon: `icons/compressed-document_red`. Colour scheme: red, matching the
  locked template, for both offerings.

## Mapping answers to the page

### Current State Summary

Write WHAT I HEARD FROM YOU in three paragraphs, sourced only from the form:

1. Who they are and what already works. Name the people, the structure, and the
   tools that hold. Give credit where the current system does its job.
2. Where things fall through. Use the client's own words for the biggest problem.
   Quote or closely echo their phrasing.
3. The blind spot underneath, plus their stated 90-day vision. Close with any
   constraint from `L/C/T8` and `L/C/T9`: if they are attached to their current
   stack or bounced off Notion before, say so plainly and note that the scope has
   to respect it.

### Phase 1: Discovery & Friction Audit

One named audit deliverable per friction area the form surfaced, apostrophe naming
with sub-bullets, per the locked template.

### Phase 2: Clear & Install

One named system per problem the client described. The name is the continuity
spine: the same name later becomes the build log question title, so make it a
clean, buildable system name (no verbs, no "We build"). Every sub-bullet must
trace back to something the client wrote on the form.

### Phase 3: Verify & Tune

Activity bullets tied to the systems from Phase 2: verify the flows the client
said were breaking, confirm reminders and automations fire, tune against the first
real cycle, transition to the ongoing subscription.

### ROI Math

If the engagement has no call data yet, do not invent numbers. Add a science
callout stating the numbers get set together on the call, then the standard label
bullets with "set on the call" values. Keep the Not Counted line qualitative and
real.

### Investment Summary (TEAMS.OS)

Source: Govindh mentorship session #76 (2026-06-25). Structure, not a fixed price:

- Anchor: $300/user/month CAD per seat.
- Team rate: volume pricing unlocks past 3 seats, scoped on the discovery call.
- Custom configuration: one-time deposit for the custom build layer, set at scoping.
- Guarantee: results-based, terms defined once the team is scoped, agreed before kickoff.

The method is guided value discovery: anchor per seat, let the client's own
hours-saved math set the value, reverse-engineer the price from there. The page
shows the anchor and structure only. For CUSTOM.OS, use the locked template's
subscription pricing instead.

### Your Custom Builds

Only include items the client actually described that sit outside the core phases.
Standard intro line from the locked template. Skip the section if nothing sourced
fits.

## Continuity rule

Phase 2 deliverable names on this roadmap become the build log question titles
verbatim (see `references/build-log-template.md`). Choose names you can ask
questions under.
