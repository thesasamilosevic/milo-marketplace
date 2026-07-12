# MILO.CUSTOM.OS Build Log (approved July 2026, revised 2026-07-11)

The client's working space for the whole build. It holds the discovery questions
worked through on the build log call and a brain dump log. There is no Loom for a
build log call. The call itself is the audit: Saša pokes holes and asks questions,
and this page gives that call its structure.

The page is shared with the client, and a client can duplicate anything shared with
them (including embedded pages) into their own workspace. So: no master templates,
no internal notes, and no unfinished system builds live on this page, ever. Systems
get built in a private build area and only the finished page gets copied into the
client's OS. Internal build planning lives on the private build page, not here
(the old Section 03 is retired).

## Inputs

Collect these before writing anything:

1. Client first and last name.
2. The client's MILO.CUSTOM.OS INSTALL ROADMAP page. Fetch it. The Phase 2
   deliverable names on that page are the source of truth for question titles.
3. The pitch call and closing call transcripts from Granola for this client.
4. The engagement's active scope: which Phase 2 deliverables are in the trial or
   first install push. This can be fewer than the full Phase 2 list.
5. Today's date as `YYYY-MM-DD`.

If any input is missing, ask for it. Never invent deliverables, client statements,
or resources.

## Page setup

- Title: `CLIENT NAME | MILO.CUSTOM.OS BUILD LOG | YYYY-MM-DD` (standard naming convention).
- Icon: `icons/new-document_red`.
- Parent: the client's DOCUMENTS page inside their Client Projects Pipeline row.

## Spaced caps convention

All red labels and question titles use spaced caps: one space between letters,
three spaces between words. Roman numerals stay compact (II, III, IV). Section
numbers read as `0 1`, question numbers as `Q 1`.

## Page structure

One header callout, then two sections.

Header callout:

```
<callout icon="/icons/science_red.svg" color="red_bg">
	> This page is your working space throughout the build<br><br>**Section 1: Initial Audit.** We will fill these in together<br><br>**Section 2: Brain Dump Log.** Drop anything in, anytime
</callout>
```

### Section 01: Auditing Prompts

Outer callout icon `/icons/die1_red.svg`, H3 title in red spaced caps
(`S E C T I O N   0 1 :   A U D I T I N G   P R O M P T S`), then a divider.

Intro callout (science_red, red_bg), quote block:

> We will fill these in together on a build log call.\<br\>\<br\>The first [N]
> questions map directly to your [trial deliverables / install roadmap
> deliverables]. The rest are [post-trial / post-install] topics we'll dig into
> once the [trial work is solid / core build is holding].

Use trial wording for trial engagements and install wording for subscription
engagements. [N] equals the count of deliverable-mapped questions in the top group,
which is the engagement's active scope. A Phase 2 deliverable outside the active
scope keeps its exact roadmap name but sits in the post-trial / post-install group.

### Question titling rule (continuity spine)

Every deliverable-mapped question title is the exact Phase 2 deliverable name from
the roadmap, in spaced caps. One question block per deliverable. What was pitched
on the roadmap is what gets asked on the build log call, under the same name.
Post-trial questions get thematic names instead, because they map to no
deliverable yet.

### Question ordering rule

At page creation, deliverable-mapped questions follow roadmap order. After the
build log call, the call wins: if a build priority was set or implied on the call,
reorder the question blocks to match it. New systems discussed on the call that map
to no existing question get retroactively added as question blocks under their
system names, after Saša confirms them. Renumber the Q labels after any reorder.

### Question block format (locked)

```
<callout icon="/icons/help-alternate_red.svg">
	### <span color="red">**Q 1 :   D E L I V E R A B L E   N A M E**</span> {toggle="true"}
		---
		<callout icon="/icons/dialogue_red.svg">
			<span color="red">**D I S C O V E R Y   Q U E S T I O N S**</span>
			---
			<span color="red">P R E - C A L L</span>
			- <span color="red">**Q1.**</span> Question one.
			- <span color="red">**Q2.**</span> Question two.
			<span color="red">P O S T - C A L L</span>
			- <span color="red">**Q3.**</span> Gap question added after the build log call.
			This feeds the [Deliverable Name] · [one line on what it becomes].
		</callout>
		<callout icon="/icons/link_red.svg">
			<span color="red">**R E S O U R C E S**</span>
			---
			<empty-block/>
		</callout>
		<callout icon="/icons/package_red.svg">
			<span color="red">**S Y S T E M   P A C K A G E**</span>
			---
			<empty-block/>
		</callout>
</callout>
```

Outer callout is always help-alternate_red. Discovery questions callout is always
dialogue_red. Resources callout is always link_red. System package callout is
always package_red. The H3 title is a toggle, and everything inside it sits one tab
level deeper.

Inside DISCOVERY QUESTIONS, two labeled groups. PRE-CALL holds the starter
questions written at page creation, mined from the form, the install roadmap, and
the pitch and closing transcripts. POST-CALL starts as a bare label; the build
analysis flow fills it with the gap questions the build log call surfaced. One
bullet per question, each prefixed with a red bold `Qn.` label, numbering
continuous across both groups. The plain-red spaced-caps group labels (P R E -
C A L L, P O S T - C A L L) are not bold. A block added retroactively for a system
that first surfaced on a call carries only the POST-CALL group.

The SYSTEM PACKAGE callout belongs on deliverable-mapped questions only, not on
post-trial thematic questions. It starts empty. After the build log call, the build
analysis flow (`references/build-analysis.md`) fills it with the build spec: build
brief, sourced facts, decisions, open items. The system itself is never built
inside it; the finished system page gets copied into the client's OS from the
private build area.

### How to write the discovery questions

Work from the transcripts before writing a single question. Pull out three things:

1. Every moment the client said they need to figure something out, decide
   something, or find something. Their own words seed the questions.
2. Every unresolved detail: numbers they guessed at, tools they were unsure about,
   people they named without context.
3. Every commitment made on the call that still needs detail before it can be built.

Then write 2 to 4 questions per deliverable under the PRE-CALL label, one bullet
per question with the red bold `Qn.` prefix, in this order:

1. Open with an easy question grounded in the client's own words from the call. A
   warm-up, not an exam.
2. Ask where the raw material lives today: accounts, tools, folders, people, rough
   volumes.
3. Probe one blind spot the client did not raise: access, exceptions, edge cases,
   who else depends on this, what breaks when it fails.
4. Close on the definition of done: the view, cadence, or output the client wants
   to see working.

End every block with a line in this shape:
`This feeds the [Deliverable Name] · [one line on what it becomes].`

Rules for the questions themselves:

- Never ask what the transcript already answers. Every question chases something unknown.
- Concrete beats abstract. Ask for counts, names, ranges like 5 to 10, and recent real examples.
- Second person, conversational, contractions welcome.
- No em dashes anywhere. Use the middle dot `·` in running text.
- No banned words or phrases.

After a build log call happens, the same rules govern the question refresh: retire
what the call answered and re-point each block at what is still unknown, sourced
from the coverage map in `references/build-analysis.md`.

### Answer capture

There is no answer section. Answers come out on the build log call, and the Granola
recording of that call is the record. After the call, drop the Granola call link
into the RESOURCES callout of each question it answered. At build time, seed
RESOURCES with any links or files the client already shared for that deliverable.
Otherwise leave the empty block.

### Post-trial / post-install topics

After the deliverable questions, add a divider, then this callout:

```
<callout icon="/icons/science_red.svg" color="red_bg">
	> These are the topics we would address [post trial / post install].
</callout>
```

Then 3 to 5 questions in the same locked block format (without the SYSTEM PACKAGE
callout), numbered continuing from the deliverable questions, with thematic titles,
plus any out-of-scope Phase 2 deliverables under their exact roadmap names. Pull
the themes from the transcripts. Recurring themes that have earned a place across
clients: the bus factor map, team hand-off map, personal operating state, personal
life friction, complexity allergy. Always end with a success metric question: 30
days out for a trial, 90 days out for a subscription. What one changed outcome
would prove the system worked?

### Section 02: Brain Dump Log

Outer callout icon `/icons/die2_red.svg`, H3 title
`S E C T I O N   0 2 :   B R A I N   D U M P   L O G`, divider, then:

```
<callout icon="/icons/science_red.svg" color="red_bg">
	> Drop anything in here, anytime. Friction, ideas, requests, frustrations, half-thoughts.<br><br>One bullet per thought is fine.
</callout>
```

Then the first dump entry: a callout (icon `/icons/litter-disposal_red.svg`)
holding a toggle whose summary reads
`B R A I N   D U M P   # 0 1 :` in red spaced caps plus a bold date mention set to
the build date. Inside the toggle: a divider and one empty bullet. Below the entry
sits a Notion template button that stamps the next numbered, dated entry in the
same format.

## Edit safety

A brand new empty page takes one full insert. Any edit to a populated page uses
targeted old_str / new_str replacements only. Never push a full content replacement
on a populated page.
