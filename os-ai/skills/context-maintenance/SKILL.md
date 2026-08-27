---
name: context-maintenance
description: >
  Use to capture and file the context from a chat before ending it, or to run a periodic
  sweep that keeps the assistant's memory, context, and rules accurate. Triggers include
  "decommission this chat", "pull the context before I close this", "capture this chat and
  file it", "run my maintenance sweep", "clean up my chats and context", "audit your memory",
  "are you still following my rules". Two modes: Decommission for one chat, Sweep for periodic
  upkeep. Proposes every delete, move, or merge and waits for approval.
metadata:
  version: "0.1.0"
  source: "Built 2026-08-20 from the chat-archive workflow. Incorporates Govindh Jayaraman's scheduled-cleanup idea and Greg Shove's agent-maintenance half hour."
---

# CONTEXT MAINTENANCE

Keep the operator's AI context clean and current. Chats pile up, context gets compressed, and rules drift. This skill runs in two modes. Decommission captures one chat before it closes. Sweep is the periodic upkeep pass. At the start, work out which mode fits. If the user is ending a single chat, run Decommission. If they ask for upkeep or an audit, or the scheduled run fires, run Sweep.

Safety rule for both modes: propose every destructive or irreversible action (deleting, moving, merging, or overwriting a file) and wait for a clear yes before doing it. Never rewrite the body of an archived transcript. Additive, reversible steps (writing a new archive file, adding a memory note) can proceed, but say what you did.

## Mode 1: Decommission a chat

Goal: pull everything durable out of a chat, file it where it will be found again, update memory, then hand the user a clean close.

Step 1. Capture the context. Produce the capture block (see "The capture template" below) for THIS conversation. Fill every field from what actually happened. Do not invent. Mark inferences with [inferred].

Step 2. File the transcript. If the workspace has a chat archive (a folder of past-chat markdown, sorted by pillar or topic), write the capture block as a new markdown file there, following the archive's existing naming, pillar routing, and any banner or decoder conventions already in use. If no archive exists yet, create one folder and start it. Match the archive's own file-naming; if unsure, ask before writing.

Step 3. Update memory. From KEY FACTS, RULES & PREFERENCES, and MEMORY DELTAS, write durable items into project memory. Add new facts, correct entries this chat superseded, retire anything it made obsolete. Flag, do not silently drop, anything that contradicts existing memory.

Step 4. Handle the working markdown. List the loose markdown files this chat produced. For each, propose one disposition and wait for the user's yes before touching it:

- Synthesize: fold it into the archive file or an existing home, then remove the loose copy.
- Delete: it was actioned, throwaway, or already saved elsewhere.
- Move to keep: still useful but the chat is closing, so move it to a keep folder where it survives.

Do nothing to any file until the user approves its disposition.

Step 5. Close. Confirm the archive file is written and memory is updated, then tell the user the chat is safe to archive or delete in the app.

## Mode 2: Maintenance sweep

Goal: a periodic pass that keeps memory, context, rules, and the archive accurate so nothing drifts. Runs on demand or on the scheduled cadence. When it runs unattended (scheduled, user not present), produce the report and a proposed action list, apply only clearly-safe additive fixes, and hold every delete, move, or merge for the user's next session.

Run these checks and report findings under each heading.

1. Rule adherence. Re-read the workspace CLAUDE.md and the rules the user has set. Sample recent work and name where the rules slipped: banned words, em dashes, naming conventions, voice, formatting, the Notion editing rules, anything the user has flagged before. List each slip beside the rule it broke, so it stops repeating.
2. Memory reconciliation. Read project memory. Find entries that are stale, contradictory, or superseded. Propose the exact add, correct, or retire for each. Apply the clear-cut additive corrections. Hold ambiguous ones for approval.
3. Context refresh. Check that the always-on context (CLAUDE.md, pillar context files, role and preference notes) still matches how the user works now. Name anything out of date and propose the update. This is Greg Shove's "update the context, fix the role document, update custom instructions."
4. Integrations. Note any connectors or tools that look broken, disconnected, or unused since the last sweep, so the user can reconnect them. This is Greg Shove's "reconnect broken connectors." You cannot reconnect them yourself, so surface them plainly.
5. Archive hygiene. Scan the chat archive for duplicates, near-duplicates, files that are fully superseded, loose files that should be synthesized, and any legacy terms not yet decoded or bannered. Propose merges and cleanups. Execute only on approval.
6. Report. Lead with a one-line state-of-context summary, then the findings under the headings above, then a numbered proposed-action list the user can approve item by item.

## The capture template

Fill this for the chat being decommissioned. State only what was actually said. Mark anything inferred as [inferred].

```
Capture only this conversation. Do not pull from memory, other chats, or anything outside what we discussed here.

TITLE: A short, plain title, in the archive's title convention.
DATE: The date or date range of this conversation. Say "unknown" if it cannot be told from the thread.
TOPIC: One line on what this conversation was about.
SUMMARY: A few sentences on what we discussed, what we decided, and why it mattered. No assumptions.
KEY FACTS: Facts about the user, their work, or their life that came up here. One line each.
RULES & PREFERENCES: Any rule, preference, or correction the user stated about how I should work. One line each. These feed memory.
OPEN THREADS: Anything unresolved, or a task left partway through.
MEMORY DELTAS: What to add, correct, or retire in project memory from this chat. Mark each ADD, CORRECT, or RETIRE.
FULL TEXT: The full conversation below this line, unedited, exactly as it happened.
```

## Notes

- This skill reads and writes the user's own workspace files and memory. It does not touch app chat history directly. The user archives or deletes the chat in the app after Decommission files the context.
- Keep the archive as the record. Synthesize and prune loose working files, but never rewrite an archived transcript's body.
- Follow the workspace's own voice and formatting rules in everything you write here.
