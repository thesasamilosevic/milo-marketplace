# Module Builder Conventions

## Legend-Aware Writing

- Client-facing steps are written so a client can understand and approve the work.
- VA-facing instructions are operational details a VA needs to execute efficiently.

### VA Callout Convention

- VA-only sections use the headset icon (`/icons/headset_blue.svg`) with a `blue_bg` callout background.
- The heading text inside a VA callout is white (unstyled). Do not wrap it in a gray or coloured span. This is intentional and matches the system legend.
- When reviewing a VA callout header that appears white on a blue background, treat it as correct. Do not flag it as a missing colour span.

### Strikethrough Convention

- Strikethrough text (`~~text~~`) on a toggle summary or label means that item is not yet ready, the technology, integration, or setup is incomplete.
- Do not flag strikethrough as an error or propose removing it. It is an intentional status indicator.

### Placeholder Convention

- Empty checkboxes (`- [ ]`) followed by a yellow warning callout indicate a step that is waiting for instructions to be written. Leave these as-is unless the user asks to fill them in.

### PinkHeader Rule

- Mark a step as PinkHeader when client presence is required, including credentials, sensitive information, or irreversible actions.

### Approval Gates

- Always ask for approval before deleting, archiving, bulk-moving, large renames, overwriting, or any action that could cause data loss or lockouts.

## Safety Rules

- Do not delete, archive, or remove data unless the user explicitly confirms.
- If a request implies deletion, present a safe alternative first, such as archive, tag, duplicate, export, or move-to-review.
- If unsure whether a step is destructive, treat it as destructive and ask.

### Structural Edit Safety

- When an edit requires re-nesting, re-indenting, or moving large blocks of content (such as wrapping multiple sections inside a new parent callout or toggle), stop and assess the risk before attempting it.
- If the edit could break page formatting, corrupt nesting, or lose content, do not attempt it programmatically. Instead, propose the structural change to the user and provide clear manual instructions (e.g. "drag Sections 01 through 06 into the Part I toggle").
- Only attempt structural edits that are small, targeted, and unlikely to cascade into formatting damage.

## Automation Awareness

For each module you draft, include a short section that:

- Identifies which sub-steps could be automated.
- Names the likely automation surface, such as specialized software prompts, Claude, or agents.
- States what inputs would be required to automate safely.

Make automation proposals executable. Always include a concrete implementation artifact, such as:

- A ready-to-copy prompt for the target tool with placeholders and example values.
- A step-by-step setup sequence someone can follow.
- A single best link to the exact product or documentation page needed.
- If you cannot execute the automation directly because the tool or integration is not available, say so and provide the do-this-next implementation steps.

## Updating Existing Modules

- Start by reading the full page and identifying the current formatting patterns already in use.
- Make the smallest possible set of edits to achieve the requested outcome.
- Preserve existing structure, icons, colours, callout nesting, and heading conventions unless the user explicitly requests a redesign.
- Never delete content. If something seems wrong or redundant, propose a change and ask for approval.

### Continuous Learning and Format Drift

- When newer modules use a newer pattern, treat the newer pattern as canonical.
- Apply the newer pattern to new work.
- Only migrate older modules if the user requests a modernization pass.

## Context Shifts and Module Splits

- Group steps that share the same objective, tool context, and dependency set.
- If steps shift to a new objective, tool ecosystem, or dependency chain, flag: the exact step where context shifts, a suggested new module title, and what should remain in the current module vs move to the new module.

## Audit Form Cross-Referencing

The MILO.LIFE.OS Audit Form lives in the Client Projects Pipeline and captures each client's digital ecosystem answers across questions Q1 through Q13. When building or updating any module in the System Installation Pipeline, always have the active client's audit form submission open for reference.

### Question Index

- Q1: Technology Hardware (Mobile)
- Q2: Technology Hardware (Computer)
- Q3: File Storage Ecosystem
- Q4: Notes, Reminders & Communication Ecosystem
- Q5: Browser Ecosystem
- Q6: Password Storage Ecosystem
- Q7: Calendar Ecosystem
- Q8: Email Ecosystem
- Q9: AI Software & LLM Ecosystem
- Q10: General Probing
- Q11: Photo Storage Ecosystem [OS+ Content Creation]
- Q12: Technology Consumption [OS+ Digital Crusade]
- Q13: Life Alignment [OS+ Focus, Align, Act]
- Each question also has sub-properties for specifics (e.g. Q3a, Q3b) and general probing follow-ups. Consult the full form schema when detail is needed

### Reference Tag Format

- Use the format `[ R E F .   Q# ]` in spaced caps when tagging a step or section to a specific audit form question, e.g. `[ R E F .   Q3 ]`, `[ R E F .   Q9 ]`
- Place the reference tag inline at the end of the relevant header or label so the client can see which of their answers informed that step
- When a step draws from a sub-question, append the letter, e.g. `[ R E F .   Q8 b ]`
- When a step draws from multiple questions, list them, e.g. `[ R E F .   Q3 ,   Q5 ]`

### When Building New Modules

- Before drafting, review the question index above and identify which audit form questions supply inputs for the module's steps
- Insert `[ R E F .   Q# ]` tags on every step or section header that depends on a client's form answer
- If a step requires the client's exact short-form answer to be read, note that explicitly, e.g. "Review the client's response to Q10b before proceeding"

### When Scanning Existing Modules

- Read through the module and identify any steps that depend on client-specific information captured in the audit form
- Where a reference tag is missing, propose adding `[ R E F .   Q# ]` and state the rationale
- Do not insert tags without confirmation, follow the same approval-before-edit rule as all other module updates

## Canonical Module Section Structure

When building or restructuring any pipeline module, follow this sequencing pattern. It was established during the AI Ecosystem module build and should be applied as the default structure for all modules going forward.

### Sequencing Principle

- Install the tools first, then configure them, then layer in knowledge and reference, then applied use
- Account setup and connectivity come before configuration
- Configuration comes before learning material
- Learning material comes before hands-on execution
- Sequential, step-by-step installation sections stay inline on the module page
- Coaching, reference, and best-practices content that would create awkward header layering inline should be broken out into subpages (same pattern as the Siri to Notion integration)

### Inline Database Pattern

- When a module references assets the client needs to retrieve (e.g. prompts, templates, rules), embed the relevant database inline near the top of the module so it can be called out in the steps below
- Example: the AI Ecosystem module has an inline AI Prompts / AI Assets database at the top; Section 2 then directs the client to retrieve the humaniser prompt from that database and add it to their Claude rules

### Non-Prescribed Tools

- Keep toggles or sections for tools the client has not been prescribed (e.g. ChatGPT, Gemini, Perplexity), they serve as future-proofing and will only be followed if explicitly assigned
- Do not remove them during reviews unless the user requests it

### Reminder: Retroactive Structure Check

- At the start of every new build session, remind the user that a retroactive structure check is pending, previously completed modules should be checked against the canonical section structure above
- This check was deferred during the initial pipeline build and should be done when the user is ready, not forced mid-session
- Flag it once at session open, then move on unless the user wants to address it
