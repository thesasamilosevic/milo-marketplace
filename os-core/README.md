# OS CORE Plugin

Extends the OS CORE package. The planning engine at the center of the system: the analytical weekly pick.

## Components

| Skill | Command | What it does |
| --- | --- | --- |
| Weekly Planning Run | `/os-core:weekly-planning-run` | Picks the week's ONE THING via a Priority Star pairwise comparison, reading open tasks, a quarterly baseline, and recent time data. |

Pairs with the Life Mentor in the `os-leadership` plugin, which runs the reflective conversation around the pick.

## Setup

Weekly Planning Run needs a connected task database (Notion action items) and optionally a time source (Rize).

> The weekly-planning scheduled runs are set up separately. Hold any data-writing run until tested by hand.

## Source

Built from the AI Assets Vault. Life Mentor moved to the `os-leadership` plugin on 2026-07-11. Tracked in the conversion map at
`projects/4.0_PURPOSE/4.4_PRODUCT_&_DISTRIBUTION/ai-assets-skill-conversion-map.md`.
