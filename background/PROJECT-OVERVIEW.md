# Project Overview — Handoff Document
*For use by any Claude instance picking up this work. Last updated: 2026-06-27.*
*Read this before reading any individual project's CLAUDE.md.*

---

## Who You Are Working With

**Diego** is building a self-improving, recursive AI-assisted development ecosystem. He is the owner of San Diego AI HELP (sandiegoai.help), an AI consulting business for San Diego small businesses. He is also developing the "Homeless Builder" brand — a YouTube channel and expanding content brand documenting the journey of building serious things with limited resources using AI tools.

**Working style:**
- Strategic thinker operating at the meta-system level, not in the weeds of individual files
- Learning web development as he goes — plain language explanations, deliberate pacing
- Organic growth is a core principle — things evolve, nothing is forced
- Path of least resistance to substantial returns
- Moving fast matters — the window for many AI-assisted development concepts is closing
- Monetization should always be a layer on every decision
- Advise first, act second — surface options before executing

**Standing rules for any Claude instance:**
- No file deletions without explicit instruction
- No permanent changes (commits, pushes, installs) without confirmation
- When uncertain whether an action is in scope, ask

---

## The Meta-System Vision

Diego is building a **recursive development ecosystem**: tools built here are used to build the next tools. Every project feeds back into the infrastructure that all future projects run on.

The architecture has three layers:
1. **Overseer** — the Claude Code instance running in `~/` (home directory). Coordinates all other instances, handles new project onboarding, spots gaps. Does not execute project-level work.
2. **Project instances** — Claude Code running inside individual project directories. Each handles its own work and logs sessions to the journal.
3. **Journal layer** — captures all machine activity across all projects. Currently flat-file (prototype); migrating to local MySQL via devlog-engine.

**Key infrastructure decisions (locked):**
- Local MySQL for all internal data — not RDS, not cloud. Owned, controlled, no external dependency.
- AWS for external/public-facing projects only (website hosting, client APIs).
- Staged automation: manual → hook-prompted → hook-drafted → autonomous. Never skip stages.
- Open-source code releases; monetize knowledge and methodology.

---

## Active Projects

### 1. sandiegoai.help — `~/my-eleventy-sdai-h/`
**What it is:** Eleventy static site for San Diego AI HELP — AI consulting for San Diego small businesses. Hosted on AWS S3 + CloudFront.

**Current state:** Active rebuild. All four industry verticals complete (Real Estate, Home Services, Healthcare, Financial Services) with landing pages and quiz flows. Homepage is an equal-industry hub. Committed and running live.

**Open items:**
- Verify quiz form submissions are arriving (API endpoint unconfirmed)
- Set up Square payment links for each service tier
- Update `/book-your/strategy-call/` to new design
- Font exploration (DM Sans is current standard, Diego wants something more distinctive eventually)
- Blog restoration for SEO (deferred)
- AWS/RDS backend to replace Calendly and API Gateway (future — do not start unless Diego initiates)

**Read before touching:** `~/my-eleventy-sdai-h/CLAUDE.md` — contains design tokens, CSS approach, site architecture, services/pricing, writing guidelines, and working-style guidance. All non-negotiable design decisions are documented there.

---

### 2. claude-journal — `~/claude-journal/`
**What it is:** The flat-file journal prototype. Documents **all machine activity** — every Claude Code session across all projects, overseer sessions, system administration, research. Serves two purposes: re-entry aid and content pipeline for Homeless Builder brand.

**Current state:** Active. Recently expanded from project-specific to machine-wide scope. `/log` slash command and `log-session` script both updated and committed.

**How logging works:**
- Git-based projects: `log-session ~/project-name` — gathers commits, summarizes, hands to `/log`
- Non-git / conversation sessions: `log-session --manual overseer` — opens editor with handoff template
- The journal instance receives the summary and writes DEVLOG.md + updates CURRENT.md

**Handoff format** (pass this to `/log` for any session):
```
Project / Activity: [name]
Date: [YYYY-MM-DD]
What happened: [2-5 sentences]
Real obstacle: [what slowed things down]
In progress when session ended: [mid-flight items]
Next action: [single clearest next step]
Open questions / blockers: [unresolved items]
Tag: [Technical] [Process] [Story] [System]
```

**Read before touching:** `~/claude-journal/CLAUDE.md` — librarian rules, file structure, entry format, tag definitions.

---

### 3. devlog-engine — `~/devlog-engine/`
**What it is:** The infrastructure project that will replace claude-journal's flat-file backend with a local MySQL database and a write script. The first explicitly recursive project — built with the meta-system, for the meta-system.

**Current state:** Planning phase only. CLAUDE.md and VISION.md written. No code yet. index.html and guide.html exist as reference documentation.

**Build sequence (do not skip steps):**
1. Run flat-file journal through real sessions — observe friction and missing fields
2. Design MySQL schema from that experience
3. Build the write script (structured summary → DB row)
4. Migrate claude-journal to use write script
5. Add overseer journal instance
6. All future projects use write script from day one

**Read before touching:** `~/devlog-engine/CLAUDE.md` and `~/devlog-engine/VISION.md` — all architectural decisions and reasoning are captured there.

---

### 4. Homeless Builder — Brand / Content
**What it is:** A YouTube channel (name only, no content yet) expanding into a full brand. The story of the journey — building serious things with limited resources using AI tools. Authentic, documentary in nature.

**Content pipeline:** DEVLOG entries from claude-journal are raw material for LinkedIn posts, blog posts, YouTube Shorts scripts, and eventually a book and course.

**Course direction:** Near-term priority. Diego may start training others soon. The methodology — recursive tooling, overseer pattern, federated journals, staged automation — is the curriculum. The DEVLOG entries written at real depth are lesson content.

**Production setup:**
- Xubuntu is the host machine; all work happens inside BunsenLabs VMs
- Screen recording: capture at the Xubuntu host level (sees all VM windows naturally)
- A separate Ubuntu VM has OBS Studio for production/editing when needed
- Starting with screencasts + voiceover (no camera required initially)
- Camera content to be introduced gradually as comfort grows

**GitHub:**
- Two accounts being created: one under the HomelessBuilder brand, one under Diego's real name
- HomelessBuilder account: open-source tools (claude-journal framework, devlog-engine, meta-system tooling)
- Personal account: professional identity
- First repos to publish: claude-journal framework, devlog-engine when ready

**Monetization model:** Open-source code + paid knowledge. Tools are free, the course teaches how to build and use them. Consulting (done-for-you for teams) is near-term revenue. Community/membership is longer-term.

---

## Key Files to Know

| File | Purpose |
|---|---|
| `~/CLAUDE.md` | Overseer context — read this every session in the home directory |
| `~/PROJECT-OVERVIEW.md` | This file — project briefing for any Claude instance |
| `~/devlog-engine/VISION.md` | Full reasoning behind the meta-system architecture |
| `~/devlog-engine/guide.html` | Human-readable system guide (open in browser directly) |
| `~/claude-journal/guide.html` | Journal system user guide (requires `journal_server.py`) |
| `~/cross-project-context-draft.md` | Superseded planning draft — can be deleted |

---

## What Was Just Accomplished (2026-06-26/27 Overseer Session)

- Overseer Claude Code instance established with full CLAUDE.md and memory
- Architecture decisions finalized: federated journals, local MySQL, AWS split, staged automation
- devlog-engine project founded with full planning documentation
- All project CLAUDE.md files updated with cross-project awareness and handoff protocol
- `/log` command updated: Project/Tags fields, System tag, accepts handoff format
- `log-session` script updated: `--manual` flag for non-git/conversation sessions
- claude-journal guide updated to match
- All changes committed in claude-journal and my-eleventy-sdai-h
- GitHub account creation in progress
- Screen recording strategy decided: Xubuntu host level, OBS VM for production

---

## Immediate Next Steps

1. Complete GitHub account setup (HomelessBuilder + personal)
2. First screen recording test from Xubuntu host
3. Website: verify quiz form submissions, commit pre-existing uncommitted changes
4. Journal: run through real project sessions to build schema intuition for devlog-engine
5. Course: begin outlining the methodology curriculum from existing DEVLOG entries
