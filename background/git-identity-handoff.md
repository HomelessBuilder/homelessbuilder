# Git Identity Configuration — Handoff to Overseer

*Written by: Homeless Builder project manager instance*
*Date: 2026-06-29*
*Action required: Overseer review and resolution*

---

## The Problem

The global git config on this machine is currently set to the `sandiegoai-help` identity:

- **Name:** sandiegoai-help
- **Email:** sandiegocloudsolutions@gmail.com

This means any project repo that does not have a local git identity override is inheriting the sandiegoai-help identity by default. This is unintended for most projects.

---

## Diego's Intended Design

Diego wants each project associated with the correct GitHub account via local git config. The intended mapping is:

| Project | GitHub Account | Name | Email |
|---|---|---|---|
| `my-eleventy-sdai-h` | sandiegoai-help | sandiegoai-help | sandiegocloudsolutions@gmail.com |
| `homelessbuilder` | HomelessBuilder | HomelessBuilder | sandiegocloudsolutions+hb@gmail.com |
| `claude-journal` | HomelessBuilder | HomelessBuilder | sandiegocloudsolutions+hb@gmail.com |
| `devlog-engine` | HomelessBuilder | HomelessBuilder | sandiegocloudsolutions+hb@gmail.com |
| overseer (`~/`) | HomelessBuilder | HomelessBuilder | sandiegocloudsolutions+hb@gmail.com |

---

## Proposed Resolution (for overseer to evaluate)

Since the majority of projects belong to the HomelessBuilder GitHub account, one clean approach is:

1. Update the global git config (`~/.gitconfig`) to the HomelessBuilder identity
2. Set a local git config override inside `my-eleventy-sdai-h` for the sandiegoai-help identity
3. Verify each other project repo either has no local override (inheriting the correct global) or set explicit local configs where needed

This minimizes the number of local overrides needed while keeping everything correctly attributed.

An alternative is to leave the global config neutral and set explicit local identities in every project — more work upfront but more explicit and less dependent on the global default.

---

## Current State of homelessbuilder Repo

- Git initialized, branch set to `main`
- Local git identity NOT yet configured (waiting on overseer guidance before first commit)
- No commits made yet

---

## Questions for Overseer

1. Which approach is preferred — update global to HomelessBuilder, or leave global neutral and set all locals explicitly?
2. Does `claude-journal` currently have a local git config set, and if so what is it?
3. Does `devlog-engine` have git initialized at all yet?
4. Does the overseer (`~/`) have git initialized?
5. Once resolved, should this handoff file be deleted or archived?
