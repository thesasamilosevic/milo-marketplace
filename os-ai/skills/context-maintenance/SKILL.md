---
name: context-maintenance
description: >
  Use to capture and file the context from a chat before ending it, or to run a periodic
  sweep that keeps the assistant's memory, context, and rules accurate. Triggers include
  "decommission this chat", "pull the context before I close this", "capture this chat and
  file it", "run my maintenance sweep", "clean up my chats and context", "audit your memory",
  "are you still following my rules". Two modes: Decommission for one chat, Sweep for periodic
  upkeep. Asks which mode to run, checks the target folders are connected first, folds durable
  pieces into the pillar memory and folders instead of writing new markdown, and disposes of
  loose files. Proposes every delete, move, or merge and waits for approval.
metadata:
  version: "0.2.1"
  source: "Built 2026-08-20 from the chat-archive workflow. Incorporates Govindh Jayaraman's scheduled-cleanup idea and Greg Shove's agent-maintenance half hour. Reworked 2026-08-28 to fold context into pillar memory and folders rather than produce transcript markdown, then 0.2.1 added the index-line requirement."
---
# CONTEXT MAINTENANCE
Keep the operator's AI context clean and current. Chats pile up, context gets compressed, and rules drift. This skill runs in two modes: Decommission captures one chat before it closes, Sweep is the periodic upkeep pass.

**Operating principle: compress, do not accumulate.** The job is to pull value out of a chat and fold it into what already exists, not to generate more files or more lines. Every pass should leave the memory and folders flat or leaner, never bigger for its own sake. Keep only what will get reused and is not already living in Notion or CLAUDE.md; if it is, link to it rather than copy it.

## Before you start
Do these two things first, in order, every run.

1. **Recommend the mode, then confirm.** Read the signals and propose a mode rather than asking cold. One chat winding down points to Decommission; a scheduled or periodic run, or an audit request, points to Sweep. Lead with the recommendation so the user confirms in one tap. Only fall back to an open question when the signals are genuinely split.

2. **Check the target folders are connected.** This skill writes into the user's own pillar folders and memory files, never into a scratch or outputs folder. Before writing anything, confirm the pillar project folders and memory are connected to the session. If they are not, ask the user to connect them and wait. Do not stage captured context in a temporary folder "for now"; it must land in its real home the first time.

Safety rule for both modes: propose every destructive or irreversible action (deleting, moving, or merging a file) and wait for a clear yes before doing it. Additive edits, like adding facts to a memory file, can proceed, but say what you did. Never rewrite the body of an archived transcript.

## What this produces
The goal is not a pile of new markdown files. It is to pull the pieces that were learned, decided, created, or changed and fold them into their existing homes:

- Durable facts and decisions go into the matching pillar memory file (`X.0-memory.md`), under the right sub-pillar heading, as short bullets with a pointer to any detail file.
- **A new memory file gets its index line in the same action.** Any memory store with an index (`MEMORY.md`, a pillar `X.0-index.md`) only surfaces what its index names. A file written without its index line is invisible to the next session, which is how a store drifts dozens of files behind. Writing the file and registering it are one step, never two.
- A piece worth keeping in full (a spec, a runbook, a schema) goes into the matching sub-pillar folder as one file, and gets one row in that pillar's `00-index.md`.
- Context or working markdown the chat already produced gets a decision: move it into the right sub-pillar folder, or delete it. Do not leave loose files behind.

Write a standalone capture or transcript file only if there is no better home and the user asks for one.

## Mode 1: Decommission a chat
Goal: pull everything durable out of a chat, fold it into memory and the pillar folders, dispose of the loose files, then hand the user a clean close.

Step 1. **Extract.** Work through the extraction checklist below for THIS conversation. Fill every field from what actually happened. Do not invent. Mark inferences with [inferred]. This is a checklist to think through, not a file to save.

Step 2. **Route.** Decide which pillar and sub-pillar each durable piece belongs to. One chat can touch several, so split the pieces by home.

Step 3. **Fold into memory.** Read the sub-pillar section first, then compress the new pieces into it. Sharpen or replace an existing bullet rather than stacking a new one beside it; most new facts are really updates to an old line. Correct entries this chat superseded, retire anything it made obsolete, and prune stale lines while you are in there so the section ends flat or leaner. Add a genuinely new bullet only when nothing there already covers it. Flag contradictions rather than silently dropping them, and report what you added, merged, and retired.

If this step creates a new memory file rather than editing one that exists, write its index line into that store's index in the same action. Never finish the step with an unregistered file. If the index cannot be written, say so rather than leaving the file orphaned.

Step 4. **Place any keeper detail.** If a piece needs its full text, save one file into the matching sub-pillar folder and add its row to `00-index.md`. If placing it means moving or overwriting an existing file, propose that and wait.

Step 5. **Dispose of loose files.** List every context or working markdown this chat produced, plus any earlier capture files sitting loose. For each, propose one disposition and wait for the user's yes:
- Move: still useful, so move it into the right sub-pillar folder and add its index row.
- Delete: actioned, throwaway, superseded, or already folded into memory.
Do nothing to a file until the user approves.

Step 6. **Close with a receipt.** Give a one-line tally of the net change: facts added, merged, retired; files moved, deleted. It makes the compression visible. Then tell the user the chat is safe to archive or delete in the app.

## Mode 2: Maintenance sweep
Goal: a periodic pass that keeps memory, context, rules, and the pillar folders accurate so nothing drifts. Runs on demand or on the scheduled cadence. When it runs unattended, produce the report and a proposed action list, apply only clearly-safe additive fixes, and hold every delete, move, or merge for the user's next session.

Run these checks and report findings under each heading.

1. **Rule adherence.** Re-read the workspace CLAUDE.md and the rules the user has set. Sample recent work and name where the rules slipped: banned words, em dashes, naming conventions, voice, formatting, the Notion editing rules, anything flagged before. List each slip beside the rule it broke.

2. **Memory reconciliation.** Read the pillar memory files. Find entries that are stale, contradictory, or superseded. Propose the exact add, correct, or retire for each. Apply the clear-cut additive corrections. Hold ambiguous ones for approval.

3. **Context refresh.** Check that the always-on context (CLAUDE.md, pillar memory and index files, role and preference notes) still matches how the user works now. Name anything out of date and propose the update.

4. **Integrations.** Note any connectors or tools that look broken, disconnected, or unused since the last sweep. You cannot reconnect them yourself, so surface them plainly.

5. **Folder and memory hygiene.** Scan the pillar folders and memory for duplicates, near-duplicates, files fully superseded, loose files that belong in a sub-pillar, and index rows that no longer match the files on disk. Propose merges, moves, and cleanups. Execute only on approval.

6. **Report.** Lead with a one-line state-of-context summary, then the findings under the headings above, then a numbered proposed-action list the user can approve item by item.

## The extraction checklist
Think through this for the chat being decommissioned. State only what was actually said. Mark anything inferred as [inferred]. This feeds the memory fold and the routing decisions; it is not a file to save unless the user asks.

```
Cover only this conversation. Do not pull from memory, other chats, or anything outside what we discussed here.
TOPIC: One line on what this conversation was about.
DECISIONS: What was decided, and why it mattered. One line each.
CREATED OR CHANGED: What was built, edited, moved, or retired (databases, files, pages, rules). One line each, with IDs or paths.
KEY FACTS: Durable facts about the user, their work, or their system that came up here. One line each.
RULES & PREFERENCES: Any rule, preference, or correction the user stated about how I should work. One line each. These feed memory.
OPEN THREADS: Anything unresolved, or a task left partway through.
ROUTING: For each durable piece above, the pillar and sub-pillar it belongs to.
DISPOSITIONS: For each loose file the chat produced, propose move (with destination) or delete.
```

## Notes
- This skill reads and writes the user's own pillar folders and memory. It does not touch app chat history directly. The user archives or deletes the chat in the app after Decommission folds the context.
- Default to folding into memory and the sub-pillar folders. A standalone transcript is the exception, not the rule. Keep one when the capture is uncertain, because the archive is insurance against a bad extraction, not a record of everything.
- Never rewrite the body of an archived transcript. Decode or banner instead.
- Follow the workspace's own voice and formatting rules in everything you write here.
