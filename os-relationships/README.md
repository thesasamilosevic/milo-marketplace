# OS+ Relationships Plugin

Extends the OS+ Relationships package. Tools for aligning the people around you with intention.

## Components

| Skill | Command | What it does |
| --- | --- | --- |
| Contacts Triage | `/os-relationships:contacts-triage` | Parses a phone contacts export into a clean, pre-sorted sheet ready for a fast tag pass. Pre-marks only the safe cuts, groups the obvious ones together, and hands every real decision back to the user. |

## Class

Review Accelerator. The skill removes the friction of the review, not the review itself. The user tags every contact. The skill never decides who stays in someone's life.

## Source

Built from Module 02-04 (Cleaning Your Contacts & Building Lead List) in the System Installation Pipeline. Tracked in the conversion map at
`projects/4.0_PURPOSE/4.4_PRODUCT_&_DISTRIBUTION/ai-assets-skill-conversion-map.md`.
The repo file is the master copy. To tune the skill, edit its `SKILL.md` and recompile the bundle.

## Setup

Needs a contacts export (a `.vcf` file) from the user's phone. The Leads-to-Notion hand-off at the end is gated to the OS+ Founder package and needs a connected Notion outreach database.
