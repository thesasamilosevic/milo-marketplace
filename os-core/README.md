# OS CORE Plugin

Extends the OS CORE package. The planning engine at the center of the system, with both halves of weekly planning: the reflective coach and the analytical pick.

## Components

| Skill | Command | What it does |
| --- | --- | --- |
| Life Mentor | `/os-core:life-mentor` | ABBI-style weekly review and alignment coaching. Reads a live published Coaching Questions & Tools library each session. |
| Priority Star Process | `/os-core:priority-star-process` | Picks the week's ONE THING via a Priority Star pairwise comparison, reading open tasks, a quarterly baseline, and recent time data. |

These two pair up: the Priority Star Process does the analytical pick, the Life Mentor runs the reflective conversation around it.

## Setup

Priority Star Process needs a connected task database (Notion action items) and optionally a time source (Rize). Life Mentor reads a public Coaching Questions & Tools library over the web, no connection required.

> The weekly-planning scheduled runs are set up separately. Hold any data-writing run until tested by hand.

## Source

Built from the AI Assets Vault, with Life Mentor migrated from the former `milo-life-os` during the os- consolidation. Tracked in the conversion map at
`projects/4.0_PURPOSE/4.4_PRODUCT_&_DISTRIBUTION/ai-assets-skill-conversion-map.md`.
