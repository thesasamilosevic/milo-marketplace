# The filing pass

A briefing that only reports leaves the person with the same inbox they woke up to. A briefing that files first hands them a shorter briefing and a smaller inbox at once. The second is worth much more, and it carries risk the first does not, because a bad rule applied every morning moves hundreds of messages before anyone notices.

This file covers how to get the rules right and how to make the first weeks safe.

## Read the inbox before you design anything

Two numbers tell you almost everything. Pull the label list and compare total messages in the inbox against unread.

- **Large total, tiny unread** means they read everything and file nothing. Filing is the whole problem. The briefing is a bonus.
- **Large total, large unread** means they have stopped opening mail. Filing helps, but the briefing is what wins their attention back.
- **Small total** means they already have a system. Do not add filing. It will fight what they do by hand.

Then pull the last two or three weeks of inbox mail and read the senders. Recurring automated senders are where the volume is, and every one you can name becomes a rule. This is more reliable than asking, because nobody can recite their own inbox from memory.

Read their existing labels too. Most people who have any labels have a structure they care about, and filing into their tree is the difference between help and vandalism. Never invent a label scheme next to one that already exists.

## Rules come from evidence, not categories

"File newsletters" is not a rule. It requires the agent to decide what a newsletter is every morning, and it will decide differently each time. A rule needs a test the agent can apply the same way twice.

Good rules key off something literal in the message: a sender address, a string in the body, a subject pattern. When you find a rule that keys off a literal string, verify it against real mail before you write it down. A rule that looked obvious and matches nothing is worse than no rule, because it fails silently.

Two traps worth naming:

**One sender, several addresses.** Mailing platforms rotate sending domains, so the same person arrives from two or three addresses. A rule built on the one you happened to see catches part of their mail and leaves the rest, which reads as the agent working badly rather than the rule being incomplete.

**Money moving in versus money moving out.** Receipts and incoming payment notifications look almost identical and belong in opposite places. Filing revenue into an expenses label quietly corrupts someone's books. Whenever a rule touches money, say which direction it applies to.

## Four things a rule can do

Every message the agent meets should land in one of these. Naming which one avoids the common failure where an agent labels something correctly and then leaves it in the inbox, which is filing that accomplishes nothing.

| Action | When |
|---|---|
| **Label and archive** | Recurring mail with a clear home. The bulk of the volume. |
| **Read, extract, archive** | Mail with occasional value inside routine packaging, like a subscription they keep for one thing it sends. Pull out what is actionable, then archive without a label. |
| **Surface, then archive** | Mail they want to know arrived and never want to see again. Deliveries, follows, confirmations. One grouped line, then gone. |
| **Do not touch** | Anything they act on directly, anything from a real person, and anything they curate by hand. |

That last row is the one people forget to ask about. Verification codes and one-time PINs belong there absolutely: archiving a code before someone uses it turns a helpful agent into an obstacle at the worst moment.

When a message matches no rule, leave it alone and surface it. An agent that guesses at unmatched mail will be wrong in ways nobody can predict, and the person will stop trusting the whole system rather than the one bad guess.

## Confirm the connector can actually write

Do this before you design a single rule, and before you promise anyone their mail will be filed.

Reading someone's inbox and modifying it are separate permissions, and a connector routinely has the first without the second. Nothing warns you. Searches work, labels list, everything looks healthy, and then every archive fails with an insufficient-scope error the moment the agent runs unattended, where nobody sees the error at all. The failure mode is the worst kind: an agent that reports "filed 14 messages" every morning while the inbox never changes.

So make one throwaway write early. Remove a label from a single message, or add one and take it back off. If it succeeds, the filing pass is real. If it fails, say so immediately and get the connector reconnected before building anything on top of it.

Two things worth knowing when it fails. Adjusting permissions is often not enough, because the session keeps the token it already holds. A full disconnect and reconnect forces a fresh consent screen, which is what actually changes the grant. And even then the running session may hold the stale token, so a new session is sometimes the only way to pick up the new one. Tell the person all of that at once rather than making them discover it a step at a time.

## Propose briefly, then act

Ship the first version in a mode where it works out what it would file, reports the plan, and changes nothing. Write the mode as one line near the top of the generated prompt so switching it is a one-word edit:

```
Current mode: PROPOSE.
In PROPOSE mode, work out what you would file, list it under "Filing plan", and change nothing.
```

Then switch on evidence, not on a calendar. **The moment two consecutive days of filing plans look right, go to ACT.** A fixed trial week sounds prudent and is usually a mistake, because a briefing that only ever proposes is a briefing that never does anything, and people stop opening it long before the trial is up. If the rules are good, that is visible by the second day.

Some rules never need a propose phase at all. A rule keyed to a literal string, like a card's last four digits, is either right or wrong on the first example, and there is nothing a week of watching will teach you. Mark those as settled in the prompt and let them act from day one.

Reporting differs by mode. While proposing, show every message and the rule it matched, because the person is auditing rules. Once acting, that detail is noise: one summary line covers it, and the briefing gets shorter, which was the point.

## Let the rule set grow itself

The rules you write on day one describe the inbox as it looked on day one. Then the person subscribes to something, signs up for a tool, starts working with a new supplier, and six months later a good share of their volume comes from senders nobody wrote a rule for. The agent keeps working, technically, while quietly doing less and less.

So build the growth in. Give the agent a standing instruction to notice automated mail that matched no rule and to raise it, without ever filing it.

### Propose when the answer is obvious, ask when it is not

This is the distinction that makes the feature work, and it is easy to miss because both cases look like "unmatched mail."

**A new recurring sender.** They signed up for a tool last week and it has started billing them monthly. What to do is obvious from what the mail is, so **propose** a specific rule: this sender, this label, archive. They answer yes and it is done.

**A long-standing sender with volume and no rule.** Order confirmations, shipping updates, account and data-access notices, calendar invitation replies. Mail they get constantly and have simply never made a decision about. Here, **ask**. Say how often it arrives and offer the plausible options, but do not presume an answer.

The reason to separate them: a proposal presumes you know what they want. A question admits you do not. Get it backward and you either bury a real decision inside a yes-or-no, or you spend their attention making them confirm something that was never in doubt. The second is annoying. The first is how an agent quietly files something the person would have wanted to see.

The tell is whether the person has ever thought about this category. Nobody has an opinion about Google's data-access notices until asked. Everyone has one about a new invoice.

### Three constraints that keep it from becoming noise

**It never acts.** Unmatched mail stays exactly where it is. An agent inventing its own filing rules is how someone's mail ends up somewhere nobody chose.

**It is silent most days.** Give it its own section and say plainly that empty is the normal case and it must never raise something just to have content. A section that exists gets filled, and a suggestion channel that cries wolf is ignored within a week. Cap it, two or three items a day at most.

**It never asks twice.** If the person did not answer, let it go. Repeating a question they skipped teaches them to skip the whole section.

Answers get written into the filing rules as ordinary rules, a one-line edit. Over a few months the rule set describes the inbox as it actually is rather than as it was the day you built it, and the person did nothing but answer a question every week or two.

## The backlog is a different job

A person with years of unfiled mail will ask you to sort it. Push back on most of that.

**Labeling a backlog is expensive and nearly worthless.** Nobody browses to a label to find a two-year-old email. They search. The labels only earn their keep going forward, where they shape what the agent files tomorrow.

**Read versus unread beats any date cutoff.** The instinct is to pick a date, but the sharper line is whether they opened it. Read means they saw it and chose not to act. Unread means they have not looked yet. Archive everything read and unstarred, leave the unread, and what remains is exactly the pile that still needs their eyes. It also lands better than a date, because nobody has to guess whether three months was too aggressive.

**Archiving a backlog is cheap and transformative**, and worth explaining properly because it sounds destructive and is not. Archiving removes a message from the inbox view. It stays in All Mail and stays searchable forever. Once someone understands that, a decision that felt frightening becomes obvious.

**Do not run a large backlog sweep through the agent.** Archiving is one write per message, so thousands of messages means thousands of calls, which is slow and can stop halfway and leave things in an unclear state. The mail client does the same job in one action. Hand the person the exact steps and let their client do it, then let the agent handle everything from that day forward. Knowing when not to be the tool is part of building a good one.
