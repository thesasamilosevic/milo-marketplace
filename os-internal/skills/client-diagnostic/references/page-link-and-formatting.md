# Page Link Syntax & Notion Formatting Spec

## Page Link Syntax (Critical)

Every inline link to a Notion page MUST use `<mention-page>`. Never use `<page>` for inline links.

- `<page>` represents a SUBPAGE on the current page. If used, it will move the target page into the diagnostic page as a child. Do not use it.
- The `url` attribute must be a compressed URL like `https://www.notion.so/4542d9f3342e4746b58a0812ac41f726` (the value returned by loadPage / search results). Never wrap URLs in `https://www.notion.so/...` and never construct synthetic URLs.
- Correct format:

```
<mention-page url="https://www.notion.so/4542d9f3342e4746b58a0812ac41f726">Page Title</mention-page>
```

- Inside colored highlight spans (Step 5 go-to lines, Step 3 module references), the mention is wrapped exactly the same way:

```
<span color="orange_bg">↳ Go to: <mention-page url="https://www.notion.so/4542d9f3342e4746b58a0812ac41f726">Review Your Current Environment</mention-page></span>
```

- To resolve the compressed URL for any pipeline step, OS+ module, or hub page, call System Installation Pipeline's data source / search the workspace by exact title and use the URL field returned. Do not invent or guess URLs.

## Notion Formatting Spec

### Outer Wrapper

The entire report lives inside one outer callout:

```
<callout icon="/icons/document_red.svg">
	...entire report content...
</callout>
```

### Color System

- Primary accent color is `red`. Step headers, category headers inside Step 1, and the info callout use `<span color="red">`.
- Step 3 (Friction Map) is entirely red: friction icons, header spans, `INSTALLATION PART:` labels, and `OS+ MATCH:` labels all use `<span color="red">`. Module-tag colors do NOT appear in Step 3.
- Step 5 module colors come from the System Installation Pipeline `Module` schema and are the ONLY place module-tag colors appear. Each Step 5 go-to line wraps `↳ Go to: <mention-page ...>` in `<span color="{color}_bg">` so the hyperlink is highlighted in the module's schema color.
- Step 7 module names use `<span color="pink">`. Pricing text is uncolored bold. Relevance labels use the color matching their tier (red = HIGH, orange = MEDIUM-HIGH, yellow = MEDIUM, green = LOW-MEDIUM, gray = LOW).

### Step Icons

Each step callout uses a fractional circle icon in red:

- Step 1: `/icons/circle-one-eighth_red.svg`
- Step 2: `/icons/circle-two-eighths_red.svg`
- Step 3: `/icons/circle-three-eighths_red.svg`
- Step 4: `/icons/circle-four-eighths_red.svg`
- Step 5: `/icons/circle-five-eighths_red.svg`
- Step 6: `/icons/circle-six-eighths_red.svg`
- Step 7: `/icons/circle-seven-eighths_red.svg`

### Science Callout (Step Description)

Each step begins with a science callout explaining what the step does:

```
<callout icon="/icons/science_red.svg" color="red_bg">
	> Description text here.
</callout>
```

### Friction Point Icons (Step 3)

Step 3 (Friction Map) stays entirely RED. Use fractional circle icons in red, `circle-one-eighth_red.svg` through `circle-alternate_red.svg`, one per friction point. The friction header span, the `INSTALLATION PART:` label, and the `OS+ MATCH:` label all use `<span color="red">`. Module-tag colors from the System Installation Pipeline are NOT used in Step 3; they apply only to Step 5.

## Step 5: Module Formatting (Queried)

Before writing Step 5, fetch the System Installation Pipeline data source schema. Read the `Module` select property's `options` array (NOT the `Submodule` property, that is a different property with different colors and is never used for diagnostic coloring). Each `Module` option has a `name` (e.g., "01 - Alignment & Foundation") and a `color` (e.g., "gray"). The `color` value from the `Module` schema is the SOURCE OF TRUTH. Use it exactly. Do not infer, guess, or substitute colors, and do not pull colors from the `Submodule` property.

### Per-Module Callout Format

1. Icon: `/icons/construction-crane_{color}.svg` where `{color}` is the option's color from the schema.
2. Header: `<span color="{color}">**{SPACED MODULE NAME}**</span>` where the module name is everything after "XX - ", converted to spaced ALL CAPS. Use the SAME `{color}` from the schema.
3. Go-to lines: Each checkbox item gets a go-to line on a SEPARATE line below it (indented one level deeper). The highlight color must be `{color}_bg` matching the module's schema color exactly:

```
<span color="{color}_bg">↳ Go to: <mention-page url="compressed-page-url">Page Title</mention-page></span>
```

### Module Header Format

```
<span color="{color}">**0 1  :   A L I G N M E N T   &   F O U N D A T I O N**</span>
```

### Fetching Page URLs

- Query the System Installation Pipeline data source for each step page by exact title. Use the returned compressed URL inside the `<mention-page url="...">` tag.
- Never construct synthetic URLs like `https://www.notion.so/...`.
- Never use `<page>` here, it would move the step page into the diagnostic.

### Sub-Sections

If a module splits into multiple sub-sections (e.g., Module 02 → Files & Notes, Communications, Contacts), create a separate callout per sub-section using the SAME module color from the schema.

## Step 7: OS+ Module Formatting

### Hub Link (Top of Step 7)

Before the first OS+ module callout in Step 7, place ONE link to the OS+ hub page (so the client can jump to the full add-ons catalogue):

```
<mention-page url="https://www.notion.so/32d739289e3a81549396e9905f90bd3b">MILO.LIFE.OS™+ ADD-ONS & EXPANSIONS</mention-page>
```

### Per-Module Callout Format

Each OS+ add-on module gets its own callout. Do NOT include a per-module page link inside the callout, the hub link at the top of Step 7 is the only OS+ page link.

```jsx
<callout icon="/icons/{icon_name}_pink.svg">
	<span color="pink">**{SPACED MODULE NAME}**</span>  -  **$ {SPACED PRICE}   C A D**
	---
	<span color="{relevance_color}">R E L E V A N C E :   {SPACED LEVEL}</span>
	{Relevance explanation paragraph.}
</callout>
```

### Key Rules

- Module name is pink and bold. Price is uncolored bold. Separated by `-` (spaces around dash).
- Do NOT add a `↳ <mention-page>OS+ ...</mention-page>` line under the header. The single hub link at the top of Step 7 is the only OS+ page link.
- The `---` divider comes directly after the module name + price line.
- Relevance label is spaced ALL CAPS with color matching the tier.
- Already-purchased modules show `Already purchased ✓` instead of a relevance label, and the explanation confirms coverage.

### Fetching Page URLs

- Search Notion for "OS+" followed by the module name (e.g., "OS+ CONTENT CREATION") and use the returned compressed URL inside `<mention-page url="...">`.
- For the hub link, use the canonical URL of MILO.LIFE.OS™+ PACKAGES (`https://www.notion.so/32d739289e3a81549396e9905f90bd3b`).

## Relevance Tier Colors

- HIGH → `red`
- MEDIUM-HIGH → `orange`
- MEDIUM → `yellow`
- LOW-MEDIUM → `green`
- LOW → `gray`

## OS+ Module Icon Assignments

- Content Creation: `playback-play-button`
- Digital Crusade: `phone`
- Travel: `airplane`
- Relationships: `network`
- Finances: `cash`
- VA Support: `headset`
- Journal: `book-closed`
- Consciousness: `infinity`
- Creativity Blueprint: `color-palette`
- Styling: `hanger`
- Physical Space Audit: `home`
- Coaching: `friends`
- Founder: `location`
- AI: `science`
