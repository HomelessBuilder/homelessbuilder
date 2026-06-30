# Session Context — Overseer / June 29–30, 2026

*Generated: 2026-06-30*
*Purpose: Full context handoff covering the June 29–30 overseer sessions*
*For use by any Claude instance picking up this work*

---

## Who You Are Working With

**Daniel Rickey (Diego)** — Owner of San Diego AI HELP (sandiegoai.help), an AI consulting business for San Diego small businesses. Content brand: Homeless Builder — a YouTube channel and expanding brand documenting the journey of building an AI services business with limited resources. Strategic thinker, learning web development as he goes, prefers plain language and deliberate pacing. Operating at the meta-system level.

**Standing rules:**
- No file deletions without explicit instruction
- No permanent changes (commits, pushes, installs) without confirmation
- Advise first — surface options before acting

---

## The Meta-System

Diego is building a recursive, self-improving AI development ecosystem. Tools built here are used to build the next tools. The overseer Claude Code instance (running in `~/`) coordinates all subordinate project instances.

**Infrastructure philosophy:**
- Local = internal. All personal tooling, journals, and infrastructure run on this machine.
- AWS = external. Public-facing projects (sandiegoai.help) live on AWS.
- Staged automation: manual → hook-prompted → hook-drafted → autonomous. Never skip stages.

---

## What Happened — June 29 Session

### Git Identity and SSH Setup
The homelessbuilder project manager instance had flagged a git identity problem via a structured handoff document (`~/homelessbuilder/background/git-identity-handoff.md`). The global git config was set to the sandiegoai-help identity, meaning most projects were being attributed to the wrong GitHub account.

**Resolution:**
- Generated ED25519 SSH key pairs for both GitHub accounts
- Wrote `~/.ssh/config` with host aliases: `github-hb` (HomelessBuilder) and `github-sdaih` (sandiegoai-help)
- Updated global gitconfig: name = "Homeless Builder", email = sandiegocloudsolutions+hb@gmail.com
- Set local override in `my-eleventy-sdai-h`: name = "San Diego AI HELP", email = sandiegocloudsolutions@gmail.com
- Both SSH connections tested and confirmed
- Resolution handoff written to `~/homelessbuilder/background/git-identity-resolution.md`

**Identity map (final state):**

| Project | Account | Name | Email |
|---|---|---|---|
| homelessbuilder | HomelessBuilder | Homeless Builder | sandiegocloudsolutions+hb@gmail.com |
| claude-journal | HomelessBuilder | Homeless Builder | sandiegocloudsolutions+hb@gmail.com |
| devlog-engine | HomelessBuilder | Homeless Builder | sandiegocloudsolutions+hb@gmail.com |
| my-eleventy-sdai-h | sandiegoai-help | San Diego AI HELP | sandiegocloudsolutions@gmail.com |

**SSH aliases:**
```bash
# HomelessBuilder repos
git remote add origin git@github-hb:HomelessBuilder/<repo-name>.git

# San Diego AI HELP repo
git remote add origin git@github-sdaih:sandiegoai-help/<repo-name>.git
```

### Git Initialized Across All Repos
All repos now have git with correct identities and initial commits:

| Repo | Notes |
|---|---|
| `~/` | Allowlist .gitignore — tracks only overseer context files |
| `~/claude-journal` | Already existed, commits current |
| `~/devlog-engine` | Initialized (was missing) |
| `~/homelessbuilder` | New project, initial commit |
| `~/my-eleventy-sdai-h` | Already existed, commits current |
| `~/monitor` | Monitoring system, runtime files excluded |

### Monitor Project
A passive monitoring system (`~/monitor/`) exists and is fully operational — running hourly via cron, writing timestamped reports to `~/monitor/reports/`, serving a browser viewer at localhost:8765. The monitor is deliberately kept invisible in overseer documentation — it is not referenced in `~/CLAUDE.md`, memory files, or `~/PROJECT-OVERVIEW.md`. The journal records that it was built; the running infrastructure does not acknowledge it.

Monitor CLAUDE.md was updated during this session to reflect that devlog-engine now has git initialized (it previously noted devlog-engine had no git repo).

### Disk Space
A disk full error had occurred earlier in the homelessbuilder session. Diego resolved it by clearing space, emptying trash, and moving unneeded directories to the host system. VM now has approximately 1GB free. Being monitored over the coming days.

### Context Files Updated
- `~/CLAUDE.md` — added homelessbuilder as active project, added Git and GitHub Infrastructure section
- `~/PROJECT-OVERVIEW.md` — full rewrite to reflect current state of all projects
- `~/MD-CATALOG.md` — expanded with homelessbuilder and monitor sections, new file entries throughout
- `~/claude-journal/CURRENT.md` — updated to reflect end-of-session state

### Journal Caught Up
All unlogged sessions were logged to DEVLOG.md:
- June 27: sandiegoai.help site documentation session
- June 29: homelessbuilder project initialization (from Diego's handoff)
- June 29: git identity and SSH setup
- June 29: git initialized on all remaining repos
- June 29: overseer context files brought current
- June 29: full overseer session wrap-up

---

## What Happened — June 30 Session

### GitHub Repositories Created and Pushed
All seven repos pushed to GitHub:

| Repo | Account | URL |
|---|---|---|
| meta-system | HomelessBuilder | github.com/HomelessBuilder/meta-system |
| claude-journal | HomelessBuilder | github.com/HomelessBuilder/claude-journal |
| devlog-engine | HomelessBuilder | github.com/HomelessBuilder/devlog-engine |
| homelessbuilder | HomelessBuilder | github.com/HomelessBuilder/homelessbuilder |
| monitor | HomelessBuilder | github.com/HomelessBuilder/monitor |
| ai-foundations-lab | HomelessBuilder | github.com/HomelessBuilder/ai-foundations-lab |
| sdai-h | sandiegoai-help | github.com/sandiegoai-help/sdai-h |

Note: `sandiegoai-help` account also has an older `sandiegoai-help` repo from early web development — candidate for archiving.

### GitHub Organization Discussion
Diego considered creating a GitHub organization and a third personal account. Resolution: the HomelessBuilder account already serves as the developer identity. No org needed at this stage. Display name set to Daniel Rickey in profile settings.

### HomelessBuilder Profile README
The `homelessbuilder` repo is a GitHub special profile repo (repo name matches account username). A profile README was written introducing Daniel Rickey and the projects. Live at `github.com/HomelessBuilder`. Tone: honest, story-driven, not marketing.

Key framing from the README:
- "I'm building a real AI services business while figuring out how to do it."
- "The tools built here are used to build the next tools."
- Lists: devlog-engine, claude-journal, meta-system, monitor

### sdai-h Made Private
The `sdai-h` repo (website source code) was made private. The business is represented by the live URL sandiegoai.help, not the code repository.

### Resume/LinkedIn Strategy
- `github.com/HomelessBuilder` in the resume header contact section as developer identity
- San Diego AI HELP represented separately via LinkedIn company profile and the live site URL
- No need for project-specific GitHub links given sdai-h is private

### AI Foundations Lab — Course Project Founded
New project `~/ai-foundations-lab/` created. A general AI literacy course for beginners with limited technical background. Hands-on lab sequence where students build a personal AI-assisted learning environment as they go.

**What the student builds:**
- A project folder with a CLAUDE.md they wrote themselves
- A personal learning journal (simplified claude-journal)
- Basic git tracking of their work
- A small project built with AI assistance
- Prompting habits that compound

**Seven-module working outline:**
1. Understanding AI Tools — conceptual groundwork
2. Your First Project Folder — Claude Code setup, first CLAUDE.md
3. The Learning Journal — first session documentation
4. Building Something Small — a real micro-project
5. Documenting and Handing Off — the recursive payoff
6. Git as a Safety Net — framed as an undo button
7. What Comes Next — advancing to higher levels

**What is NOT in this course:** MySQL, multiple GitHub accounts, SSH management, AWS, monitor/cron systems, the overseer pattern.

**Adaptation model:** Themed versions (trading, healthcare, etc.) go in `/adaptations/` and are built only after the general course is stable. An AI trading version is the likely first adaptation for a specific prospective student.

Files created:
- `CLAUDE.md` — project manager instructions
- `VISION.md` — founding decisions and adaptation model
- `INSTRUCTOR-VISION.md` — founding framing for the AI instructor persona (see below)

### AI Instructor Concept — Founded
An AI instructor with a defined name and persona will serve two unified roles:

**Role 1 — Course Developer:** Takes creative ownership of developing curriculum, as if the concept belongs to it. Has pedagogical opinions and a consistent voice. Diego retains final authority.

**Role 2 — Student Guide:** Guides students through labs during the course. Same persona who built the course teaches it.

**Drift prevention principles (locked):**
1. Diego holds final authority — instructor proposes, Diego approves
2. The persona serves the student — every decision evaluated against beginner needs
3. Course vision is fixed — instructor works within VISION.md framework
4. Instructor has opinions, not autonomy — surfaces tradeoffs, does not act unilaterally

**What is not yet decided:**
- The instructor's name (the next decision — unlocks everything else)
- Teaching style and personality
- Student delivery method (Claude Code locally? Claude.ai project? Custom deployment?)
- Instructor backstory (optional)

`INSTRUCTOR-VISION.md` was written and committed to `~/ai-foundations-lab/` to lock in this framing before development begins.

---

## Current Project State (End of June 30 Session)

### Active Projects

| Project | Directory | Status | GitHub |
|---|---|---|---|
| San Diego AI HELP site | ~/my-eleventy-sdai-h | Live on AWS, active maintenance | sdai-h (private) |
| claude-journal | ~/claude-journal | Functional, current | claude-journal |
| devlog-engine | ~/devlog-engine | Planning phase, no code yet | devlog-engine |
| homelessbuilder | ~/homelessbuilder | Early foundation | homelessbuilder |
| ai-foundations-lab | ~/ai-foundations-lab | Founded, ready for PM session | ai-foundations-lab |
| meta-system (overseer) | ~/ | Active, all context current | meta-system |
| monitor | ~/monitor | Operational, running hourly | monitor |

### Open Items

**Website (my-eleventy-sdai-h):**
- `og-image.jpeg` → rename to `og-image.jpg` before next deploy
- Square payment links not set up on service pages
- Legacy pages pending cleanup (/book-your/ subdirs, /with/, /to/, /join-us/)

**Homeless Builder:**
- Episode one script and press release both unreviewed (~1 month)
- Recording format and on-camera decision still open

**AI Foundations Lab:**
- Name the instructor — the next decision
- Write instructor's CLAUDE.md once name and teaching style are defined
- Begin curriculum development in PM session

**devlog-engine:**
- MySQL not yet installed — intentionally deferred
- Schema design awaiting real session friction to surface needs

**GitHub:**
- sandiegoai-help/sandiegoai-help (old repo) — candidate for archiving

---

## Key Files Reference

| File | Purpose |
|---|---|
| `~/CLAUDE.md` | Overseer context — read every home directory session |
| `~/PROJECT-OVERVIEW.md` | Master project briefing for any Claude instance |
| `~/CENTRAL-VIEWER-REFERENCE.md` | Architecture plan for unified documentation viewer |
| `~/ai-foundations-lab/VISION.md` | Course founding decisions |
| `~/ai-foundations-lab/INSTRUCTOR-VISION.md` | AI instructor framing — read before developing the instructor |
| `~/devlog-engine/VISION.md` | Meta-system architecture reasoning |
| `~/homelessbuilder/background/git-identity-resolution.md` | Full git identity and SSH resolution record |
| `~/claude-journal/DEVLOG.md` | Full session history — all machine activity |
