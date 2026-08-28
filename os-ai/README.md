# OS+ AI Plugin

Extends the OS+ AI package. Tools that make AI itself easier to use well.

## Components

| Skill | Command | What it does |
| --- | --- | --- |
| Prompt Architect | `/os-ai:prompt-architect` | Builds a prompt, scores it out of 10 on five criteria, and iterates with you until it is sharp. Includes a fill-in starter template. |
| Transcript Organizer | `/os-ai:transcript-organizer` | Turns a raw voice-note transcript into a clean, structured map of topics, ideas, action items, and gaps. |
| Context Maintenance | `/os-ai:context-maintenance` | Captures and files a chat's context before you end it (Decommission), or runs a periodic upkeep sweep on memory, context, rules, integrations, and the archive (Sweep). Proposes every delete, move, or merge and waits for approval. |

## Source

Built from the AI Assets Vault prompts, per the conversion map at
`projects/4.0_PURPOSE/4.4_PRODUCT_&_DISTRIBUTION/ai-assets-skill-conversion-map.md`.
The repo file is the master copy. To tune a skill, edit its `SKILL.md` and recompile the bundle.
