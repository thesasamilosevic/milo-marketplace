# Audit Process, Description Protocols, and Form Safety

## Database Stewardship, Purpose

- Audit databases for naming, descriptions, icons, templates, views, and maintainability
- Output approval-ready recommendations only (no automatic changes)
- Preserve system-wide consistency while respecting per-database exceptions

## Non-Destructive Rules

- Never delete pages, rows, properties, or views
- Never change property types
- Never rename anything automatically
- Flag high-impact changes (e.g. renaming a heavily-used property)

## Audit Output Format

Output only items requiring changes (no internal reasoning). Use sections in order, skipping empty sections:

1. Properties
   - Descriptions: `Property | Current | Suggested`
   - Names: list rename suggestions only
   - Auto property names: use generic names and drop database-specific prefixes. The database name already provides context, so properties should not repeat it (e.g. "Description" not "Belief Description", "Event" not "Life Event")
   - Property icons: description and text-type properties should use the information icon (info-alternate). Flag any missing or mismatched property icons for manual correction (cannot be set via API)
   - Status nomenclature (names and colours) must match the tutorial/legend
   - Fully generic descriptions: property descriptions must not reference specific tag names, option values, other column names, or database-specific items. The property name and database name already provide context. Tag names are always visible in the dropdown, so the description should not repeat them
   - Single quotes rule applies only to maintenance prompts (agent-facing), not property descriptions
   - Evergreen descriptions (no dependency on tag lists, other properties, or anything that may change)
   - Copy rule: reuse descriptions verbatim when a property has the same function across databases
   - Relations naming: use "Related 'Database Name'" format, dropping suffixes (Vault, Pipeline, etc.)
   - Rollup naming: use "Source 'Master Property' Rollup" pattern (e.g. "Life 'Master Pillar' Rollup") to make rollup origin and aggregation explicit
   - Remove pre-framing wording (e.g. "Upgrade item" becomes "Item/Topic" when the database name already frames it)
2. Database title and icon
3. Views
4. Templates (review/create; recommendations only)
5. Tags / select colouring
6. Automations
7. Open-page field order (recommendations only)
8. Maintenance instructions and "prompt to maintain"

## Templates (Audit Checklist)

- Make or review database template (create if missing, optimise if present)
- Nomenclature and iconography consistency. Relations should use the related database's icon (or sub-icon) when applicable
- Flow: order fields in natural fill sequence (big picture to granular)
- Minimise clicks: propose automation/AI-filled fields, flag unnecessary fields as candidates for removal
- Universal/yellow databases may need multiple pillar-colour template variants
- Automation naming convention: simple numbering (e.g. "Automation 1", "Automation 2")

## "Prompt to Maintain" (per database)

- For databases where it applies (e.g. Recipes), create a paste-ready prompt that lets a user submit info via chat and have it fully tagged/filled
- Ask follow-up questions only when required fields are missing

## Sequential Audit Process (per database)

### Phase 1, Scan & Present

Load the database and its Database Maintenance Vault row. Review every item below in order. Present the findings in a single scannable table covering all 17 checklist items, with columns: Item / Status / Observation / Recommendation. Mark compliant rows with a check and items needing changes with a warning. Below the table, list optional improvements and any questions before the user confirms scope. Use the same table structure for the Phase 3 close so output is consistent end-to-end.

1. Templates. If missing, build one or prompt the user to create one. If present, review for accuracy, optimisation, and performance. Ensure template content reflects the current schema and workflow
2. Nomenclature and iconography. Must be consistent across databases. Relations use the related database's icon. Property names are auto/generic (no db-specific prefixes). Certain icons are assigned system-wide to mean certain things; follow the established icon conventions
3. Flow / ease of use. Data columns should be ordered in the natural fill sequence: large picture to small picture, getting more granular as you go. The flow should match how you think when entering data
4. Minimise clicks / editing. Reduce clicks wherever possible. If a field can be automated with an AI column, propose it. If a piece of data is unnecessary, flag it as a candidate for removal
5. Multiple template needs. Universal/yellow databases need templates in yellow plus all pillar colours (green, blue, red, purple). Other databases may need one template per entry type
6. Default template. If there are multiple templates or types, consider which should be the default for each view. Ensure the default matches the view's filter
7. Automations. Flag for manual check (cannot view via API). Check that all automations follow the naming protocol: 'Automation 1', 'Automation 2', etc. Each lives within its database
8. Auto-tagging and automation opportunities. Consider how the database could auto-tag or automate data filling. Look at what automations exist, what data is in there, and how recurring templates or AI fills could reduce manual work. Only suggest automations that are possible within Notion's current capabilities. Notion database automations can trigger on: page added, property changed. They can act on: edit property, add page to database, send notification, send Slack message, or run AI actions. There is no trigger for page content edits. Always include specific automation suggestions for every database during audit
9. Pre-framing language. If the database name already frames the content (e.g. 'System Upgrades Pipeline'), column titles should not repeat it (e.g. 'Upgrade Item' becomes 'Item' or 'Topic')
10. Status nomenclature. Status option names and colours must match the nomenclature in the tutorials and legend page
11. Descriptions. All properties must have fully generic, evergreen descriptions. No references to specific tag names, other columns, or database-specific items (these may change). If the same property function exists in another database with a description already written, reuse that description verbatim
12. Open-page field order. Flag for manual check (cannot set via API). Recommend ideal order: large picture to granular, matching the fill sequence
13. Relation naming. Use "Related 'Database Name'" format for all relations, dropping suffixes like Vault or Pipeline (e.g. "Related 'Hero's Journey'" not "Related 'Hero's Journey Vault'"). Life pillar relations use "Related 'Life Pillar(s)'"
14. ABBI text box / bullet points. Flag for manual check. If a template has an ABBI/science callout, ensure bullet points are actual bullets, not dashes
15. Tag colouring. All tags rainbow (orange, yellow, green, blue, purple, pink, red, then loop back to orange). Never use grey, default, or brown. When adding a new option to an existing property, continue the sequence from the last colour used
16. Spelling and grammar. Across all property names, descriptions, option names, view names, and database contents
17. Maintenance prompt. Agent-facing instructions in the 'Database Maintenance Vault' row. Must enable data entry from anywhere in the system via chat. The agent extracts, tags, and enters data; asks for missing required fields; the user never needs to be in the database to add a complete entry

### Phase 2, Execute

User reviews Phase 1 findings and approves which changes to make. Execute only approved changes. One database at a time. Before applying changes, set the maintenance row Status to 'Updating'. After Phase 3 verification, flip Status to 'Updated'.

### Phase 3, Verify & Close

After all changes are applied: reload the database, confirm every checklist item against the instruction rules, present a final checklist table showing done / manual for all 17 items, confirm any maintenance prompt is in the 'Database Maintenance Vault' row, and mark the database as complete.

## Database Description Protocol

This module defines how ABBI writes database descriptions across MILO.LIFE.OS™. Descriptions must be consistent, evergreen, structurally aligned, and written in ABBI's voice.

Core principles: Function first (begin by explaining what the database does). Scope second (specify what is stored, tracked, or organised inside). Purpose last (end with the outcome or benefit). Keep descriptions evergreen, neutral, and system focused.

Structure rules:

- Opening phrases: ABBI alternates between three approved openers: "This lives in...", "You'll find this in...", "Part of...".
- Sentence construction: use periods to separate ideas. Do not use em dashes. Give each thought its own sentence. Keep sentences concise but complete. Aim for three to four sentences per description.
- Final sentence: end with the outcome, role, or benefit. Example patterns: "Your master task list connected to projects and goals." "The feedback loop that turns intention into measurable progress."

Content rules: explain the role of the database (function), what is inside (scope), what this enables or improves (purpose). Use page mentions for single pillar databases and data source mentions for databases spanning pillars. Mention related databases when this clarifies relationships (Tasks to Projects, Recipes to Groceries & Supplements, Knowledge Topics to Media Vault). Keep connections natural, not forced.

Tone and voice: conversational, direct, clear. No jargon, no corporate language, no motivational tone, no sales tone. Include function, scope, purpose. Avoid workflow explanations, implementation instructions, time specific references, and buzzwords. Never include the system name MILO.LIFE.OS (or any variant such as MiloOS, Milo.Life.OS, Milo Life OS) in a database description. The system name is implied by context and adds no descriptive value.

Terminology: use "integrate" instead of "onboard". Use "guiding goals" when referencing North Star supporting goals. Use "North Star" only for the overarching vision. Use consistent OS terms: Pillars, Pipelines, Vaults, Life Pillars, MiloOS. Do not use "Pensieve". Do not use "onboarding".

## Life Pillar Description Framework

This module defines how ABBI writes the "Hey, it's ABBI!" descriptions for the Life Pillars inside MILO.LIFE.OS™. Every pillar description follows four parts:

1. Opening framing. One to two sentences. Defines what this pillar is about in plain language. Names the core function. Example patterns: "Life Design is about...", "Energy is the foundation that...", "Purpose is where you bring...".
2. Deeper purpose. One to three sentences. Explains why this pillar matters to your identity and long-term direction. Links the pillar to highest potential, freedom or stability, harmony or fulfilment, legacy or long-term impact. Tone stays calm, grounded, and neutral.
3. Scope of this space. One to three sentences. Explains what this page is for inside the OS. Clarifies what belongs here and what should live elsewhere. Uses patterns like "This page is where you design...", "Here you create practices for...", "This space helps you...".
4. "Here you'll keep your..." list. Five to seven bullets. Each bullet is a concrete artefact or workflow that lives in this pillar. Focus on documents, database views, routines, protocols, checklists, and trackers.

Tone and voice: write in second person ("you"). Keep tone calm, direct, and grounded. Maintain a neutral-warm presence. Avoid hype, sales language, or motivational clichés. Emphasise clarity, intention, and steady action. Keep language simple and concrete.

What to avoid: step-by-step workflows or SOPs, time-bound language (dates, launches, current projects), personal stories or emotional processing, hype language ("crush", "level up", "grind"), implementation details that belong in databases, checklists, or playbooks. Descriptions must stay evergreen, system-level, and focused on function, scope, and purpose.

## Form Editing Safety

### Never Replace the Questions Array

- When editing a Notion form view (FormEditorView), do not issue a single `set` on the entire `questions` array of an existing form
- A full-array replacement silently overwrites every hand-applied rich-text formatting inside question descriptions (bold, links, line breaks the user added in the UI)
- Use targeted `replaceString` edits scoped to one field at a time, typically only the `name` of one question, or one specific substring inside one `description`
- Always `loadDatabase` immediately before any form edit to capture the user's latest manual state
- If a bulk rename or reorder is requested, do it via a sequence of surgical edits, not a full-array `set`

### MILO.LIFE.OS Audit Form

- The active audit form lives on the Client Projects Pipeline database
- Form view title: MILO.LIFE.OS Audit Form
- Q63 (Health & Training Workflow Friction [OS+ PHYSIOLOGY REBUILD]) is intentionally removed from the form. Do not reinstate it. The underlying property may remain in the schema, but it must not appear in the form's `questions` array
- Question label format is `Q## · M## : Title` (zero-padded, module prefix). Q01 and Q02 are intake and carry no module prefix
- Question descriptions contain manually-applied bolding and formatting. Treat them as preserved content. Never bulk-overwrite
- Section breaks are added manually in the Form Builder UI. The FormEditorView API surface does not expose section-break entries in the `questions` array, so they cannot be created or edited programmatically
- Conditional logic, when present, blocks API edits to the entire form. Conditional rules are re-applied manually by the user after structural changes
- Form question titles and descriptions do not render markdown. Writing `**bold**`, `*italic*`, `[link](url)`, etc. into a form question's `name` or `description` via the API will appear to clients as literal asterisks / brackets, not formatted text. Bold and other rich-text formatting in form questions must be applied by the user in the Form Builder UI. Never attempt to apply markdown formatting to form question fields via `updateDatabase`
- Form view titles and descriptions (the form-level header, not per-question) may render markdown, but per-question fields do not
