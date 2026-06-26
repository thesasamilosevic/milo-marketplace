# Edit Strategy & Safety Rules

## Edit Strategy (Avoid Timeouts)

All edits to a populated diagnostic page must be applied as targeted `oldStr` + `newStr` replaceString operations on `updatePage`. Never push a full-content replacement on a page that already has content, those calls routinely time out and get cancelled.

- Default mode: targeted `replaceString` edits, each scoped to the smallest unique block needed (a single line, a single callout, or a single paragraph).
- A brand-new empty diagnostic page can be filled with one full-content insert. A populated page cannot.
- Cap each `updatePage` call at roughly 25 contentUpdates. If the planned edit set is larger, split into sequential batches and run them one after another (never in parallel on the same page URL).
- Between batches, briefly re-orient against the latest page state before issuing the next batch.

## Safety Rules

- Never invent client data. If a field is missing, log it under "Unanswered Questions" in Step 1.
- Always quote the client's own words when mapping friction points.
- Always fetch the live schema before writing Step 5; do not hardcode module names or colors.
- Always filter Goods & Services Vault by `Status = Active` before writing Step 4.
- For revising or fixing an existing diagnostic, ALWAYS use targeted `oldStr` + `newStr` replaceString operations on `updatePage`. Never push a single full-content replacement on a populated page (it routinely times out). Split large edit sets into sequential batches of ~25 contentUpdates each.
- Always use `<mention-page url="compressed-url">Title</mention-page>` for inline page links. Never use `<page>` (which moves the target into the current page) and never wrap URLs in `https://www.notion.so/...`.
- For Step 5, the `Module` select property's `color` value from the schema is the source of truth (NOT `Submodule`, that is a different property and must never be used for Step 5 coloring). Apply the `Module` color exactly to the icon, header span, and `_bg` highlight spans, never substitute, guess, or pull from `Submodule`.
