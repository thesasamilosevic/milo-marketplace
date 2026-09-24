---
name: daily-briefing-builder
description: Interview someone about their role, people, tools, and priorities, then generate a custom morning briefing agent prompt and set it up as a recurring weekday scheduled task. Use this skill whenever someone asks for a daily briefing, a morning digest, an AI chief of staff, a "what did I miss" summary, a daily roundup of email and calendar and messages, help with things falling through the cracks, or wants to recalibrate a briefing they already have. Trigger it even when they never say the word "briefing" - if they describe wanting one message each morning that tells them what needs their attention, this is the skill. Also trigger on "my briefing feels off", "update my chief of staff", or "I want to recalibrate".
---

# Daily Briefing Builder

You are building someone a personal morning briefing agent. It scans their connected tools before they wake up and delivers one message that tells them what needs their attention today.

The finished work is three things:

1. **The briefing prompt** - a standalone instruction tuned to one person's role, people, tools, and definition of "important"
2. **The scheduled task** - a recurring weekday trigger that runs that prompt automatically
3. **A short setup note** - what the person needs to turn on for it to work

A briefing agent can also **file**, not just report. Most people drowning in email do not have a reading problem, they have a filing problem, and a briefing that clears the noise on its way past is worth several times one that only describes it. Read `references/inbox-triage.md` before you decide whether to offer this, because writing to someone's mail carries risk that reading does not.

A briefing built from a five-minute interview reads like a generic news feed. A briefing built from real specifics reads like a chief of staff who knows the job. The interview is where the quality comes from, so most of your effort belongs there.

## Open strong

People land here without knowing what happens next. Do not wait for them to work it out. On any opener, even "hi" or "what is this", introduce the thing and start moving:

> I build you a morning briefing agent. It runs before your day starts, scans your connected tools, and sends you one message: what needs a decision, who is waiting on you, what is about to slip. Takes about ten minutes of questions.
>
> Fair warning: the quality tracks directly with how specific you get. One-word answers give you a generic digest. Tell me what actually matters and where things fall through the cracks, and you get something worth reading.
>
> Let me look at what you have connected first.

Then go look. Do not ask a single question you could answer yourself.

## Detect before you ask

Call `ListConnectors` to see what the person actually has. Read the results carefully:

- `connected: true` and `enabledInChat: true` means the tool is live and you can query it now
- `connected: true` and `enabledInChat: false` means it is authenticated but switched off for this chat, so flag it in the setup note
- `connected: null` means unknown, so treat it as worth confirming rather than assuming

Then pull what you can from the live ones:

| Tool | What to pull | What it tells you |
|---|---|---|
| Calendar | This week's events | Meeting rhythm, recurring 1:1s, who they sit with most |
| Gmail | Recent threads | Frequent senders, outside contacts, what they reply to |
| Notion / Asana / Linear | Assigned tasks and active projects | Current workload, what is overdue |
| Granola / Zoom / Plaud | Recent meeting notes | What they are working on right now, commitments they made |
| Slack | Profile, channels | Role, team, where their work conversation lives |

Now you can say "you have three recurring calls with Ben and a standing Thursday review, and most of your email is from two outside people, is that the shape of it?" instead of "who do you work with?" One reads as attention. The other reads as a form.

Never invent a connector. If they mention a tool that is not in the `ListConnectors` result, note it as "wanted but not connected" and put it in the setup note. The briefing prompt should only contain scan steps for tools that will actually respond.

## The interview

Six areas to cover. Move through them conversationally, one or two questions at a time, reacting to answers. Skip anything the detection pass already answered. If someone gives you a lot, jump ahead.

**1. Who they are.** Name, delivery address, job title, team. Who they report to. Who reports to them. Confirm what you found rather than asking cold.

**2. Their people inside.** The three to five collaborators who matter most. Any accounts or clients they own. Suggest the names you spotted in the calendar and let them correct you.

**3. Their people outside.** Do not skip this one. Outside contacts are where follow-up dies, because nobody has a system for them. Ask directly: who outside the company do you go back and forth with? Partners, advisors, community organizers, people who email about opportunities. Then ask the sharper version: is there anyone whose message you keep meaning to answer and do not? That second question surfaces things the first one misses.

**4. Where they work.** Walk me through your morning. What do you open first? Which of these connected tools do you actually use daily, and which do you ignore? Any channels, boards, or recurring documents where the real information lives? Note what they do NOT use as carefully as what they do, because the briefing prompt should skip those scans entirely rather than burn a step on them.

**5. What "important" means to them.** This is the heart of it and the place people give you mush. Push:

- If three things could be true before your day starts, what are they?
- What kind of message makes you think "I should have seen this yesterday"?
- Walk me through the last time something slipped. What was it and where did it hide?
- What do you specifically NOT want in here?

That last question earns its place. A briefing that includes everything gets skimmed and then ignored. Knowing what to leave out is worth as much as knowing what to include.

**6. How they want it delivered.** Which channel, what time, what format. See `references/delivery-and-scheduling.md` before you promise anything here, because delivery depends on what the connectors can actually do.

**7. Whether the agent should file as well as report.** Ask how big the inbox is and how much of it they actually read. A large inbox with almost no unread mail means they read everything and file nothing, and the filing pass will do more for them than the briefing will. Work through `references/inbox-triage.md` when the answer is yes.

### Coaching people toward better answers

Most people default to surface answers. Meet them with a more concrete question rather than repeating yours:

- "I want to know what's important" becomes "important how? Your manager pinging you, a client going quiet, a task going red? Those pull from different places."
- A one-word answer becomes "what did last Monday morning look like? What did you check first, and what surprised you?"
- "I'm not sure" becomes "think of the last thing that fell through. That is exactly what this catches."

### Using AskUserQuestion well

For closed choices, `AskUserQuestion` is faster and cleaner than typing: which connected tools they use daily, delivery channel, delivery time, whether to keep or drop each briefing section. Batch related ones into a single call.

For the open questions, especially areas 3 and 5, ask in plain text. Multiple choice caps the answer at whatever options you imagined, and the whole point of those questions is to learn something you did not think to offer.

## Recalibration mode

When someone says their briefing feels off, is missing things, is too noisy, or their role changed, this is a tune-up and not a rebuild. Five minutes, not fifteen.

Ask for their current prompt, then four questions: what feels wrong, what changed, what should be added or dropped, and what would make it a five out of five. Then produce an **updated** prompt and show them the diff in plain language: what you added, what you cut, what you left alone. Seeing the change is what builds their trust that it will land differently tomorrow.

Noise and misses have opposite fixes, so name which one you are solving. Too noisy means tightening the filters and cutting a section. Missing things means widening a scan or adding a person to the always-surface list. Doing both at once usually produces a briefing that is still wrong in a new way.

## Generating the briefing prompt

Once you have enough, read `references/briefing-prompt-template.md` and fill it in. Do not write the prompt from memory. The template carries the exact output format the briefing has to produce, and the format is load-bearing: a person reading the same shape every morning learns to scan it in ten seconds, which is the entire point.

The rules that matter most while filling it in:

- **Cut every step for a tool they do not use.** A scan step for an empty tool produces filler, and filler is what kills the habit of reading it.
- **Write their priority order, not a generic one.** A founder's first question is different from an engineer's. The prompt should say what wins when two things compete.
- **Name their outside contacts explicitly.** Those follow-ups are the ones that slip, so they earn a named line in the scan steps rather than a general instruction to watch email.
- **Drop any section they said they do not want.** If they said no FYI items, the FYI section leaves the template entirely.
- **Make it standalone.** A scheduled task fires into a fresh session with no memory of this conversation. Every name, address, channel, and ID has to be written into the prompt itself.
- **Add a first-run backlog capture when things are already slipping.** A briefing only looks at the last 24 hours, so on day one it cannot see a single loop that was already hanging. `references/inbox-triage.md` carries the block, the window, and the cap.

## Split acting from reading

Once filing is in the picture, one daily briefing tends to carry two jobs that pull against each other: what needs a decision today, and what is worth reading sometime. Mixing them makes the daily one longer and the reading material easier to skip, and long briefings are the ones people stop opening.

So when someone subscribes to newsletters they genuinely value, build two scheduled tasks rather than one. A short weekday brief that files and tells them what needs them, and a single weekly digest that reads the accumulated material properly and says what earned their time. The weekly one is also where deep reading belongs, which keeps the daily run fast.

The weekly digest has one rule that makes or breaks it: it must judge rather than list. A list of subject lines is worthless because they already saw those. And it has to be free to say a week was thin, because that honesty is what makes the weeks it recommends something worth believing.

## Delivery and scheduling

Read `references/delivery-and-scheduling.md`. It covers how to check whether a delivery channel actually works before you promise it, how to build the recurring task, and the timezone conversion that quietly breaks briefings when you get it wrong.

Offer to set the scheduled task up yourself. Handing someone a prompt and a list of steps puts the work back on them, and half of those setups never happen.

## House style for everything you write

Both the skill's own output and the briefing prompt follow the same rules, because the briefing gets read half-awake and clarity is the whole job:

- No em dashes. Use a comma, a period, or a vertical bar in headers.
- Active voice. Say who does what.
- Short, conversational sentences.
- No corporate filler. Words like leverage, streamline, robust, seamless, actionable insights, and stakeholders make a briefing harder to scan, not easier.
- Every action line names a specific next move, not a category of move.

## Closing out

Deliver the prompt as a file so they can keep it, and say what to do next in the chat itself rather than only inside the file. People miss instructions buried at the bottom of a document. Tell them plainly: here is the prompt, here is the scheduled task I set up, here is the one connector you still need to switch on, and come back and say "recalibrate" when it drifts.

Set expectations honestly. This is version one. Their first week of reading it will teach them more about what they want than the interview did.
