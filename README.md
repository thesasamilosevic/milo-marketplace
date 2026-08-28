# MILO Marketplace

Claude plugins for MILO, package-aligned to the OS+ catalog. Seven plugins, fourteen skills.

Each plugin maps to a package a client can buy. Install the whole marketplace and the skills group themselves by package in Claude's `/` menu, so `os-content` skills sit together, `os-founder` skills sit together, and so on.

## What's inside

| Plugin | Skills |
| --- | --- |
| `os-core` | Life Mentor, Priority Star Process |
| `os-content` | Script Converter, Content Editor & Coach, Caption & Title Writer, Shot List Director |
| `os-ai` | Prompt Architect, Transcript Organizer |
| `os-founder` | Marketing Copy, SWOT Analysis, SOT Analysis |
| `os-leadership` | Meeting Summarizer, EA Task Creator |
| `os-finances` | Shopping Strategist |
| `os-vitality` | Music Librarian |

### What each one does

**os-core** is the spine. Life Mentor runs the reflective half of weekly planning, the coaching conversation when you feel stuck or off track. Priority Star Process runs the analytical half, a pairwise tournament that picks the week's ONE THING. They pair up.

**os-content** carries a video from idea to publish. Script Converter turns a voice memo into a script. Content Editor & Coach gives feedback on the draft without rewriting it. Shot List Director breaks the script into shots. Caption & Title Writer writes everything you publish around the video.

**os-ai** sharpens how you work with AI. Prompt Architect builds and scores prompts. Transcript Organizer turns a brain dump into structured thinking.

**os-founder**, **os-leadership**, **os-finances**, and **os-vitality** each carry the skills for their package: ad and email copy, meeting summaries and delegation checklists, purchase research, and music discovery.

Four skills run two modes, long-form and short-form. Say which one you want when you invoke them. Their `/` descriptions spell it out.

## What is not inside

Instructions for building inside Notion do not live here. They live in the **ABBI Metadata Vault** in Notion, because that is the only place both readers can reach: Claude through the connector, and the Notion agent natively. Keeping a second copy here would mean maintaining the same rule twice and watching the copies drift.

The split: instructions for how to *think* live in this repo as skills. Instructions for how to *build in Notion* live in the vault.

## Installing

Two ways in. Pick one, not both.

**From GitHub** (recommended). Add the marketplace once, then pull updates whenever a version ships:

```
thesasamilosevic/milo-marketplace
```

Add it under Customize → Plugins → Browse → Add marketplace. Access rides on GitHub permissions, so a private repo needs the person added as a collaborator.

**From a local folder.** Drag the folder onto the plugins screen. Claude reads it directly and never checks GitHub, so every change needs another drag. Useful while building a skill, awkward as a habit.

Running both at once is the trap: the local copy wins, GitHub goes stale, and nothing tells you they disagree.

## Shipping an update

1. Edit the skill files.
2. Bump the plugin's `version` in its `.claude-plugin/plugin.json`, and the marketplace `version` in `.claude-plugin/marketplace.json`. **The version bump is what signals a new release.** Without it, nothing updates.
3. Commit and push.
4. Refresh the marketplace in Claude, then restart.

If you installed from a local folder instead, steps 3 and 4 do nothing. Drag the folder again.

## Structure

```
.claude-plugin/marketplace.json     the manifest, lists every plugin
os-<package>/
  .claude-plugin/plugin.json        name, version, description, keywords
  README.md                         what this plugin holds
  skills/
    <skill-name>/
      SKILL.md                      frontmatter plus the instructions
      references/                   optional, loaded on demand
```

A skill's `description` frontmatter is what Claude reads to decide whether to reach for it, and what you see in the `/` menu. It earns its length. Write it as the phrases someone would actually say.
