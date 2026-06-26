# Diagnostic Task (7 Steps)

## Step 1: Form Readout

Structured dump of every intake form response, organized by environment category. Each category gets its own sub-callout with a category-specific icon in red. Categories: Hardware, File Storage, Notes & Tasks, Browser, Passwords, Calendar, Email, AI & Automation, Photo & Content Storage, Technology Limits, Life Alignment (including Q10 sub-parts a–f), Unanswered Questions.

Quote the client's words directly. Note which options they selected and which they did not.

## Step 2: Current State Summary

One paragraph in plain language. Address the client by first name. Paint the picture of where they sit right now across their digital ecosystem. No bullet points.

## Step 3: Friction Map

Identify 6–8 friction points from the intake data. Each gets a numbered sub-callout with a fractional circle icon. For each friction point:

- Step 3 stays entirely red. Use red for every visual element in this section: fractional circle icon (`circle-..._red.svg`), header span (`<span color="red">`), `INSTALLATION PART:` label, and `OS+ MATCH:` label. Mentions inside Step 3 are plain (no `_bg` highlight wrappers). Module-tag colors are not used here, they only appear in Step 5.
- Quote the client's exact words that revealed it.
- Explain why it matters in plain language.
- Add an `INSTALLATION PART:` label, then link directly to the matching pipeline step page using `<mention-page url="compressed-page-url">Step Title</mention-page>`. Resolve the URL by querying the System Installation Pipeline data source for the exact step title.
- If an OS+ module addresses the same friction, add an `OS+ MATCH:` label and link to the OS+ module page using `<mention-page url="compressed-os-plus-page-url">OS+ Module Name</mention-page>` with price and purchased status if applicable.
- Never use `<page>` here, only `<mention-page>`.

## Step 4: Tech Stack Prescriptions

Three tiers: Tier 1 (high-value switches), Tier 2 (secondary switches), Tier 3 (future discussion). Plus an "Already Aligned" section for tools that need no change. Each item is a checkbox with the tool name and what it replaces or accomplishes. Pull the approved tool list from the Goods & Services Vault (`Status = Active`).

## Step 5: Installation Prescription

The full installation sequence. Query the System Installation Pipeline schema for module names, colors, and order. For each module, create a callout with the module's schema color applied to the construction-crane icon, header text, and go-to background highlights. The `↳ Go to: <mention-page ...>` link MUST be wrapped in `<span color="{color}_bg">` so the hyperlink renders highlighted in the module's schema color. Each installation step is a checkbox with a description of what it accomplishes for this specific client, followed by a go-to line linking to the actual pipeline step page.

## Step 6: Future State Summary

One paragraph describing the client's life once the full Core installation is complete. Address by first name. Paint the after picture that mirrors Step 2's before picture. No bullet points.

## Step 7: Future Opportunities

Begin Step 7 with a single link to the OS+ hub page placed BEFORE any module callouts: `<mention-page url="https://www.notion.so/32d739289e3a81549396e9905f90bd3b">MILO.LIFE.OS™+ ADD-ONS & EXPANSIONS</mention-page>`.

Then list every OS+ add-on module. Order by relevance (highest first, already-purchased last). Each module gets its own callout with: pink bold module name + dash + uncolored bold price, relevance label in spaced ALL CAPS with tier color, and a paragraph explaining why this module does or does not match the client's form data. Do NOT add a per-module `<mention-page>` link inside the callout, the single hub link at the top of Step 7 is the only OS+ page link.
