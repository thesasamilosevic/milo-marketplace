# OS Internal Plugin

Not package-aligned. The build-and-deliver and OS-maintenance tools, kept together because they serve no single sellable package. Renamed from the former `milo-internal`, and absorbing the formatting and maintenance skills from the former `milo-life-os`.

## Components

| Skill | Command | What it does |
| --- | --- | --- |
| Client Diagnostic | `/os-internal:client-diagnostic` | Produces the 7-step diagnostic report from a client's intake form and pushes it to their Notion diagnostic page. |
| Client Documents | `/os-internal:client-documents` | Builds the locked Coaching Agreement and Leader Install Roadmap deliverables to their approved templates. |
| Module Builder | `/os-internal:module-builder` | Drafts and refines System Installation Pipeline modules with client-facing steps and VA execution notes. |
| Page Formatter | `/os-internal:page-formatter` | Applies the MILO house style to a Notion page: heading architecture, callouts, bullets, colour rules. |
| System Maintenance | `/os-internal:system-maintenance` | Audits and standardises MILO databases, writes descriptions, and safely edits Notion forms. |

## Source

Migrated from `milo-internal` and `milo-life-os` during the os- consolidation. Tracked in the conversion map at
`projects/4.0_PURPOSE/4.4_PRODUCT_&_DISTRIBUTION/ai-assets-skill-conversion-map.md`.
The repo is the master copy. To tune a skill, edit its `SKILL.md` and recompile the bundle.
