# MILO.CUSTOM.OS Build Analysis (approved July 2026)

Runs after a build log call. The build log opened the loop; this closes it. Read
the call transcript, map what it answered against the build log, and stage each
system package for the build. The output is a build spec per system, not a built
system: Saša drafts the build from the spec, Claude refines the finer elements on
request.

## Inputs

Collect these before writing anything:

1. Client first and last name.
2. The client's MILO.CUSTOM.OS BUILD LOG page. Fetch its full current state. Never
   work from memory of it.
3. The client's MILO.CUSTOM.OS INSTALL ROADMAP page. The Phase 2 deliverable names
   are the system list.
4. The Granola transcript of the build log call. If more than one call exists, take
   all of them.
5. Today's date as `YYYY-MM-DD`.

If any input is missing, ask for it. Never invent client statements, numbers,
tools, names, or decisions. Every fact must trace to a transcript, the build log,
or the install roadmap.

## Step 1: Read

Read 100% of the transcript before writing anything. A long transcript gets read
in chunks until nothing is left.

## Step 2: Coverage map · review before any page edit

For each question block on the build log, report in chat:

1. Status: ANSWERED, PARTIAL, or NOT DISCUSSED.
2. Facts: numbers, names, tools, prices, volumes · the client's own words where
   they help.
3. Decisions agreed on the call.
4. Open items: what the call left unresolved, phrased as the next question to ask
   the client.
5. New systems: anything discussed on the call that maps to no existing question.
   Flag these as candidate additions to the build log; Saša confirms before they
   go on the page.
6. Priority: any build order the call set or implied, quoted from the transcript.

Nothing touches Notion until Saša approves this map.

## Step 3: Stage each system package

After approval, fill the SYSTEM PACKAGE callout inside each answered question
block with a build spec, red spaced-caps labels, in this order:

- `B U I L D   B R I E F` · one line on what gets built.
- `S O U R C E D   F A C T S` · the facts a builder needs, each traceable to a
  source.
- `D E C I S I O N S` · what the call locked.
- `O P E N   I T E M S` · unresolved details that block the build, phrased as the
  questions that would close them.

The spec is client-visible; it describes their system in their words. The system
itself is never built on the shared page, because a client can duplicate anything
shared with them. Build home: the client build area in the business workspace once
that workspace is connected; until then, a private page in Saša's workspace,
outside anything client-shared. The finished system page gets copied into the
client's OS.

## Step 4: Restructure, log, and link

1. If the call set a build priority, reorder the question blocks to match it and
   renumber the Q labels.
2. Add confirmed new systems as question blocks under their system names.
3. Write the gap questions under each block's POST-CALL label, one bullet per
   question with the red bold `Qn.` prefix, numbering continued from the PRE-CALL
   group. PRE-CALL questions stay untouched as the record of what was asked
   (question-writing rules live in `references/build-log-template.md`).
4. Drop the Granola call link into the RESOURCES callout of every question the
   call answered.
5. Update the systems-built memory: one line per staged system with client, system
   name, status, and what it retrofits from an earlier client build.

## Step 5: Retrofit check

Before speccing any system from scratch, scan the systems-built memory for a
matching system already built for another client. A match means the spec starts
from that build and lists only the deltas.

## Edit safety

Any edit to a populated page uses targeted old_str / new_str replacements only.
Never push a full content replacement on a populated page.
