# OS+ Leadership Plugin

Extends the OS+ Leadership package. For people who develop other people: clean notes and clear delegation.

## Components

| Skill | Command | What it does |
| --- | --- | --- |
| Meeting Summarizer | `/os-leadership:meeting-summarizer` | Pulls meeting transcripts for a date range, filters to one meeting type, and writes one structured entry per meeting into the user's meeting-log database. |
| EA Task Creator | `/os-leadership:ea-task-creator` | Turns a spoken instruction or Loom transcript into a precise, Notion-ready execution checklist for a VA. |

## Setup

Meeting Summarizer needs a connected transcript source (Granola, or similar) and a Notion meeting-log database. The meeting-type filter, target database, and field mapping are configured per meeting type at first run. It pulls only from the transcript and never invents content.

> Scheduling is held until the user has run it by hand and confirmed the output. Nothing writes to a vault on a schedule until then.

## Source

Built from the AI Assets Vault prompts, per the conversion map at
`projects/4.0_PURPOSE/4.4_PRODUCT_&_DISTRIBUTION/ai-assets-skill-conversion-map.md`.
The repo file is the master copy. To tune a skill, edit its `SKILL.md` and recompile the bundle.
