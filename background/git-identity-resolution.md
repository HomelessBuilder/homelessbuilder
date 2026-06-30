# Git Identity Resolution — Overseer Handoff

*Written by: Overseer instance (~/)*
*Date: 2026-06-29*
*Resolves: background/git-identity-handoff.md*

---

## Status: Resolved

All issues identified in `git-identity-handoff.md` have been addressed. This document
records what was done so the project manager instance has a complete picture.

---

## What Was Done

### 1. SSH Keys Generated

Two ED25519 key pairs now exist at `~/.ssh/`:

| File | Account |
|---|---|
| `id_ed25519_homelessbuilder` | HomelessBuilder GitHub account |
| `id_ed25519_sandiegoaihelp` | sandiegoai-help GitHub account |

Both public keys were added to their respective GitHub accounts and tested.
Authentication confirmed for both.

### 2. SSH Config Written

`~/.ssh/config` defines two host aliases:

```
Host github-hb       → authenticates as HomelessBuilder
Host github-sdaih    → authenticates as sandiegoai-help
```

When adding a remote to any repo, use the alias instead of `github.com`:

```bash
# HomelessBuilder repos (this project, claude-journal, devlog-engine)
git remote add origin git@github-hb:HomelessBuilder/repo-name.git

# San Diego AI HELP repo (my-eleventy-sdai-h only)
git remote add origin git@github-sdaih:sandiegoai-help/my-eleventy-sdai-h.git
```

### 3. Global Git Config Updated

`~/.gitconfig` now uses the HomelessBuilder identity:

- **Name:** Homeless Builder
- **Email:** sandiegocloudsolutions+hb@gmail.com
- **Default branch:** main

This is the correct global default. All repos except `my-eleventy-sdai-h` inherit it.

### 4. Local Override Set — my-eleventy-sdai-h Only

`~/my-eleventy-sdai-h` has a local git config override:

- **Name:** San Diego AI HELP
- **Email:** sandiegocloudsolutions@gmail.com

No other project needs a local override.

### 5. Git Initialized in All Projects

| Repo | Status |
|---|---|
| `homelessbuilder` | Initialized, initial commit made |
| `claude-journal` | Already initialized, commits current |
| `my-eleventy-sdai-h` | Already initialized, commits current |
| `devlog-engine` | Initialized (was missing), initial commit made |

---

## Identity Map (Final State)

| Project | GitHub Account | Name | Email |
|---|---|---|---|
| `homelessbuilder` | HomelessBuilder | Homeless Builder | sandiegocloudsolutions+hb@gmail.com |
| `claude-journal` | HomelessBuilder | Homeless Builder | sandiegocloudsolutions+hb@gmail.com |
| `devlog-engine` | HomelessBuilder | Homeless Builder | sandiegocloudsolutions+hb@gmail.com |
| `my-eleventy-sdai-h` | sandiegoai-help | San Diego AI HELP | sandiegocloudsolutions@gmail.com |

---

## What the Project Manager Should Know Going Forward

- Never set `user.name` or `user.email` locally inside `~/homelessbuilder/` — the global
  config is already correct and will be inherited automatically.
- When pushing to GitHub for the first time, use `git@github-hb:HomelessBuilder/homelessbuilder.git`
  as the remote URL (repo name on GitHub may differ — confirm with Diego).
- The `git-identity-handoff.md` file in this folder is now historical record.
  No further action needed on the issues it raised.
