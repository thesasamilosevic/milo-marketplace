# MILO Marketplace

A plugin marketplace for the MILO.LIFE.OS plugins. Hosting this as a git repo lets
people add it once and pull updates whenever you publish, with no re-sending of files.

## What's inside

| Plugin | For | Skills |
| --- | --- | --- |
| `milo-life-os` | Clients (their own system) | Life Mentor, Page Formatter, System Maintenance |
| `milo-internal` | You only | Client Diagnostic, Module Builder, Client Documents |

The manifest is `.claude-plugin/marketplace.json`. Each plugin lives in its own
folder in this repo, referenced by a relative `source` path.

## Private repo and access

Host this as a private GitHub repo. Both plugins live in it, which is fine for your
own use since you own the repo.

There is no shareable secret link for a git-based marketplace. Access rides on GitHub
permissions, not a public URL. So:

- For your own use, it just works. You are the owner, so `/plugin marketplace add`
  uses your authenticated GitHub.
- To give a specific person access without making the repo public, add them as a
  collaborator on the repo (or issue a fine-grained access token or deploy key
  scoped to it). Once they have read access, they add the marketplace the same way.
- If you ever want clients to self-serve `milo-life-os` without repo access, that
  is the case for a separate public marketplace listing only the client plugin. Say
  the word and I will build that split.

## Publish (one time)

From this folder:

```bash
git init
git add .
git commit -m "MILO marketplace v1.0.0"
git branch -M main
git remote add origin https://github.com/<your-username>/milo-marketplace.git
git push -u origin main
```

## How people add it and install

```
/plugin marketplace add <your-username>/milo-marketplace
/plugin install milo-life-os@milo-marketplace
```

You install the internal one the same way:

```
/plugin install milo-internal@milo-marketplace
```

## Publishing an update

1. Edit the skill files in the plugin folder.
2. Bump the plugin's `version` in its `.claude-plugin/plugin.json`, and the
   marketplace `version` in `.claude-plugin/marketplace.json`.
3. Commit and push.
4. Installed users refresh with `/plugin marketplace update`, then update the plugin.

The version bump is what signals there is a new release.
