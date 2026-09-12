# Delivery and scheduling

Two things break briefings after a good interview: promising a delivery channel that does not work, and setting a schedule in the wrong timezone. Both are avoidable in about two minutes.

## Check delivery before you promise it

"Connected" and "can send" are different claims. Many email connectors read mail and create drafts without exposing a send action. Confirm what the tools can actually do before you tell someone their briefing will land in their inbox at 7am.

Look at the real tool list for their connected apps. A connector with `create_draft` but no send tool cannot mail them anything.

Ranked options, best first:

**1. Scheduled task notifications.** `create_trigger` takes a `notifications` object. Set `{push: true, email: true}` and the run summary reaches their phone and their inbox with no email connector involved at all. This works for nearly everyone, so make it the default and add other channels on top rather than instead.

**2. A real send action.** If they have a connector that genuinely sends mail, or a Zapier "send email" action they have switched on, use it. This gives the cleanest inbox result and full control of the subject line. Confirm the action exists before writing it into the prompt.

**3. A draft in their inbox.** If the email connector only drafts, the briefing becomes a draft addressed to them. It sits in their drafts folder rather than arriving as a new message, so pair it with push notification and tell them where to look. This is a workable fallback and a poor primary.

**4. A message to themselves in their chat tool.** Slack or Teams DM. Works well for people who open chat before email. Bot messages do not always push reliably, so keep push notification on alongside it.

Whatever you pick, write the actual mechanism into step 7 of the briefing prompt. "Send via email" is not an instruction a fresh session can follow. Name the tool and the address.

If nothing sends, say so plainly rather than shipping a prompt that silently fails every morning. Notification-only delivery is still a working briefing.

## Building the scheduled task

Use `mcp__claude-code-remote__create_trigger`. Never use the local cron tools. Those run inside the current session and vanish when it ends, which means the person's briefing quietly never fires and nobody finds out for a week.

Three things to get right:

**The prompt is standalone.** Each firing starts a fresh session with no memory of the interview. Paste the entire briefing prompt into the trigger's `prompt` field. Not a summary, not a pointer to a document. The whole thing.

**The cron runs in UTC.** Convert from their local time using the offset in effect, and shift the day field if the conversion crosses midnight.

| Their time | Their zone | UTC offset | Cron |
|---|---|---|---|
| 7:00am weekdays | America/Toronto (summer) | -4 | `0 11 * * 1-5` |
| 7:00am weekdays | America/Toronto (winter) | -5 | `0 12 * * 1-5` |
| 6:30am weekdays | America/Los_Angeles (summer) | -7 | `30 13 * * 1-5` |
| 8:00am weekdays | Europe/London (summer) | +1 | `0 7 * * 1-5` |
| 5:00pm weekdays | America/Denver (summer) | -6 | `0 23 * * 1-5` |

Say the local time back to them before you create it. "This fires at 7:00am your time, Monday through Friday" catches a bad conversion in one second.

**Daylight saving shifts it.** Cron is fixed UTC, so a briefing set in August arrives an hour early or late come November. Mention it once when you create the task and tell them to say "shift my briefing an hour" when the clocks change. A briefing that shows up at 6am unannounced is how people turn these off.

Name the task something they will recognize in a list, like `Morning Briefing | [Their Name]`. Set `notifications` to `{push: true, email: true}` unless they asked otherwise.

## Ask when they do admin, and build for that slot

Most people want this in the morning, and morning is the right default. But ask anyway, because the answer changes the document rather than just the clock: "when do you actually sit down and clear your inbox?"

Some people do not open email until the end of the day. For them a morning brief is half wasted, reporting on an overnight sliver to someone who will not act for ten hours. The evening slot has a real advantage too: a full day of material to work from.

Build whichever slot they name. The two are genuinely different documents.

**Morning build.** Looks forward. Section A is today's schedule, with the high-stakes meetings marked and the unprepared ones flagged while there is still time to prepare. Meeting commitments come from yesterday's calls. The window covers overnight, and on Monday it reaches back across the weekend. Language is "decide today."

**Evening build.** Looks backward. Section A is the meetings they had today, listed as context for the follow-ups below rather than as a schedule to prepare for, because the day is over. Meeting commitments come from today's calls, hours old rather than a day old. The window runs evening to evening. Language is "decide tonight."

The mistake to avoid is building an evening brief that reports on tomorrow. It feels helpful and it is not what the person asked for: someone doing end-of-day admin wants to close out the day they just had, not start planning the next one. Ask which they want, then commit to it.

Say the slot back to them in plain words before you create anything. "This lands at 6:45pm and covers the day you just finished" catches a misread in one sentence.

Note that a `CRON_TZ=` prefix on the cron expression pins the schedule to their timezone rather than UTC, which removes daylight saving drift entirely. Prefer it wherever the scheduler accepts it.

## Match the model to the job

A scheduled task runs every weekday forever, so its model is a recurring cost the person never sees. Set it deliberately. But be careful which work you call cheap, because the obvious answer is usually wrong.

**The genuine cheap-model job is the one-time backlog sweep.** Thousands of identical archive calls, no judgment in any of them, and nobody should be doing it by hand. That is where a small model belongs and where the savings are real.

**The recurring daily run is not that job**, even though the filing half looks mechanical. Deciding that an incoming payment is revenue rather than an expense, that a client going quiet after a proposal matters more than an overdue task, that a contract being voided is worth a line, all of that is judgment wearing the costume of pattern matching. Cheapen it and the brief still arrives, still looks well formed, and is quietly wrong in ways nobody can catch, because there is nothing to compare it against.

The same holds doubly for a weekly reading digest, whose entire job is deciding what earns someone's attention. A cheaper model hedges, paraphrases the subject line, and recommends everything.

So the rule is not "recurring means cheap." It is: spend where a wrong answer is invisible, save where the work is provably mechanical. Say the reasoning out loud when you set it, because a client running this for their team will ask what it costs to operate.

## Fire it once before you leave

Run `fire_trigger` on the new task so they see a real briefing today rather than finding out tomorrow whether it works. This is the single highest-value step in the whole build, because the first real output is what tells you the filters are wrong while you still have the context to fix them.

Then ask what they would change about it. One round of adjustment against real output beats another ten minutes of interview questions.

## The setup note

Short, in the chat, not buried in a file. People do not scroll to the bottom of documents. Cover:

- Where the briefing arrives and at what time, in their local time
- Anything they need to switch on: connectors that are authenticated but off for scheduled runs, tools they mentioned but have not connected
- What happens if a connector drops out, which is that the briefing runs with a gap rather than failing outright
- That version one is a starting point, and to come back and say "recalibrate my briefing" when it drifts

Send the briefing prompt itself as a file too. They will want to read it, edit it, and keep it somewhere.
