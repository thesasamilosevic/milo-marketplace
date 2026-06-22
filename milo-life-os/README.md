# MILO.LIFE.OS (Client Plugin)

Skills a client runs on their own installed MILO.LIFE.OS system.

## Components

| Skill | Command | What it does |
| --- | --- | --- |
| Life Mentor | `/life-mentor` | Runs the ABBI Weekly Review and Planning session and alignment coaching. |
| Page Formatter | `/page-formatter` | Enforces the system's heading, callout, list, and colour rules across any page. |
| System Maintenance | `/system-maintenance` | Audits databases against the 17-point checklist, writes database and Life Pillar descriptions, and protects forms from unsafe edits. |

## Setup

These skills operate on the user's connected Notion workspace. Connect Notion so the
skills can read pages, fetch data source schemas, and apply targeted edits. System
Maintenance uses the current user's own Database Maintenance Vault.

## Usage

Type `/` and pick the command you want. Each skill loads its detailed reference files
on demand.

## Extending

The intended next additions are OS+ usage skills and the system installation step
skills, so a client can run as much of their own setup as possible. They drop into
`skills/` without touching the existing three.
