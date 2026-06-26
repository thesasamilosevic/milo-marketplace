# OS+ Vitality Plugin

Extends the OS+ Vitality package. Energy and environment tools.

## Components

| Skill | Command | What it does |
| --- | --- | --- |
| Music Librarian | `/os-vitality:music-librarian` | Keeps a living catalog of listening habits, audits playlists, and hands over a fresh batch of close-match and stretch tracks each session, grounded in real Spotify data. |

## Setup

Requires a connected Spotify account. The skill reads recent plays, top artists, and liked songs, and works against a music catalog page the user maintains (a Notion page or doc). It never invents tracks or links, and never writes to the catalog without confirmation.

## Source

Built from the AI Assets Vault prompt, per the conversion map at
`projects/4.0_PURPOSE/4.4_PRODUCT_&_DISTRIBUTION/ai-assets-skill-conversion-map.md`.
The repo file is the master copy. Runs on a custom cadence the user triggers, not a fixed schedule.
