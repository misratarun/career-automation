# Multi-Agent System for Personalized Career Knowledge Work Automation
## Project CLAUDE.md — Decision Audit Trail & Context

> Synthesized from architectural planning session (March 2026).
> Update this file after every major decision or learning session.
> Global personal context (career, values, goals) lives in ~/.claude/CLAUDE.md — this file layers on top.

---

## Project Identity

**Title:** Multi-Agent System for Personalized Career Knowledge Work Automation
**Subtitle:** Agentic Workflow System for Intelligent Resume Optimization and Job Search Strategy
**Purpose:** Dual-use — personal job search tool AND portfolio project demonstrating multi-agent AI systems to hiring managers at AI companies.

**Owner:** Tarun Misra — PM/TPM/TAM/Technical Consultant, 14+ years enterprise delivery.
Targeting customer-facing technical roles at AI companies (remote, US).
Career assets repo: https://github.com/misratarun/career-assets

---

## Architecture: Two-Phase Incremental Build

### Phase 1 — Intelligent Automation (Resume Optimizer)
Build first. Ship fast. Use immediately for actual job applications.

**What it does:**
- Reads all 7 years of DOCX resumes from local folder
- Reads GitHub career-assets repo
- Takes a job posting as input (text, PDF, or URL)
- Generates ATS-optimized core skills and position-specific bullets
- Calculates skill match percentage (resume vs. job posting)
- Updates a Google Doc (baseline resume template) with: profile summary, core skills, position bullets

**Important distinction:** Phase 1 is intelligent automation, NOT agentic. Claude executes instructions in sequence but does not make autonomous decisions or iterate based on feedback.

**Estimated build time:** 4–7 days at 4 hours/day

### Phase 2 — Autonomous Career Agent (Agentic Layer)
Builds on top of Phase 1. Adds true agentic behavior.

**What it adds:**
- Autonomous job board monitoring (finds relevant postings without being prompted)
- Strategic role evaluation against personal goals and values
- Skill gap analysis and preparation suggestions
- Learning feedback loops: tracks interview outcomes, refines job match scoring
- Evaluation framework with performance metrics

**What makes it "agentic":** Makes autonomous decisions, evaluates outcomes, adjusts course without human intervention per step.

**Estimated build time:** 7–9 days at 4 hours/day (after Phase 1 is complete)

---

## Agent Roles

**Phase 1 — Three agents in parallel:**
1. **Resume Analyzer Agent** — reads all DOCX files, extracts skill and achievement patterns across 7 years
2. **Job Matcher Agent** — analyzes job posting, maps requirements, scores match percentage
3. **Document Updater Agent** — updates Google Doc via Google Workspace MCP

**Phase 2 adds:**
4. **Job Board Monitor Agent** — autonomous scraping and role evaluation
5. **Strategy Agent** — evaluates role fit against personal goals and career values

---

## Technical Stack Decisions

| Component | Decision | Reason |
|---|---|---|
| DOCX parsing | Claude native Document Skills | Production-grade; handles structure, styles, metadata |
| Google Docs integration | Google Workspace MCP server | Claude Code calls it like a built-in tool; no custom REST/OAuth code |
| Job input | Text paste or URL | Simplest approach for Phase 1 |
| Orchestration | Claude Agent SDK (Phase 2) | Enables spawning parallel subagents |
| Auth | Claude Pro ($20/month) | Cost-effective for heavy daily use vs. API ($200–400/month) |

---

## Inputs Required

- [ ] Local folder path containing 7 years of DOCX resumes
- [ ] Career-assets repo cloned locally: https://github.com/misratarun/career-assets
- [ ] Google Doc URL — baseline resume template
- [ ] Google Workspace MCP authentication (one-time OAuth setup)
- [ ] Job posting (text/URL) per run

---

## Context Management Strategy

**Web Claude (claude.ai):** Thinking, brainstorming, architecture decisions, learning agentic concepts. Web Memory enabled for persistent cross-session context.

**Claude Code (terminal):** Building and execution. Reads this CLAUDE.md at every session start.

**Bridge:** After web Claude sessions, document key decisions here. Ask Claude: "Add today's learnings to my project CLAUDE.md."

---

## Portfolio Framing

> "Built a two-phase multi-agent system demonstrating intelligent automation scaling to autonomous decision-making. Phase 1: Resume analysis agent reads 7 years of career documentation, evaluates job postings, generates ATS-optimized content, and updates Google Docs with skill-match scoring (40–50 hours manual work → 2–3 minutes per role). Phase 2: Autonomous agents monitor job boards, evaluate role fit against personal goals, identify skill gaps, and learn from interview outcomes — creating a self-improving career guidance system."

**Key portfolio elements to document as you build:**
- Architecture diagram — how agents communicate and coordinate
- Evaluation methodology — how success is measured at each phase
- Performance benchmarks — time saved, accuracy, match % accuracy
- Emergent Phase 2 behaviors — decisions the system makes that weren't explicitly programmed

---

## Evaluation Framework (Phase 2)

- Resume-to-job skill match percentage (primary metric)
- Strategic role fit score (alignment to personal goals)
- Skill gap delta (missing skills vs. required)
- Interview callback rate (feedback loop input for self-improvement)

---

## Owner Constraints & Values

- Outcome ownership > task execution
- Customer impact focus
- Remote US roles only
- Phase 1 must be immediately usable for active job search
- Building simultaneously as personal tool and portfolio demonstration

---

## Open Questions / Next Decisions

- [ ] Which job boards to monitor in Phase 2? (LinkedIn, Greenhouse, Lever, etc.)
- [ ] How to store and feed interview feedback into the learning loop?
- [ ] Google Doc update strategy — full resume replace, or section-by-section?
- [ ] Confirm local folder path for DOCX resumes before starting Phase 1 build

---

## Decision Log

| Date | Decision | Rationale |
|---|---|---|
| 2026-03-26 | Phase 1 before Phase 2 | Immediate utility + solid foundation for agentic layer |
| 2026-03-26 | Multi-agent over monolithic | Parallel processing, portfolio value, industry-standard pattern |
| 2026-03-26 | Google Docs via MCP | Zero custom integration code needed |
| 2026-03-26 | DOCX as source format | Native Claude Document Skills; preserves formatting and structure |
| 2026-03-26 | Claude Pro over API | $20/month vs. $200–400/month for daily heavy use |
| 2026-03-26 | Incremental build (Phase 1 → Phase 2) | Each phase usable immediately; reduces risk of over-engineering |
