# MILO.LIFE.OS Internal Plugin

Saša's build-and-deliver tools. Not for client distribution.

## Components

| Skill | Command | What it does |
| --- | --- | --- |
| Client Diagnostic Analyst | `/client-diagnostic` | Produces the 7-step diagnostic report from a client's intake form and pushes it to their Notion diagnostic page. |
| Module Builder | `/module-builder` | Drafts and refines System Installation Pipeline modules with client-facing steps and VA execution notes. |
| Client Documents | `/client-documents` | Builds the locked Coaching Agreement and Leader Install Roadmap deliverables to their approved templates. |

## Setup

These skills operate on a connected Notion workspace. Connect your Notion account so
the skills can fetch pages, read data source schemas, search by title, and apply
targeted edits. The skills reference live data sources by name, including the System
Installation Pipeline, the Goods & Services Vault, the Client Operations Pipeline,
and the System Packages Vault.

## House rules applied across all skills

- Brand name: MILO.LIFE.OS.
- Document titles: name first, `CLIENT NAME | DOCUMENT TYPE | DATE`, all caps.
- Trademark: plain `™` in body text, never the emoji, never in titles.
- Notion edits: targeted old_str / new_str edits only. Never a full-content replace
  on a populated page.

## Usage

Type `/` and pick the command you want. Each skill loads its detailed reference files
on demand.
