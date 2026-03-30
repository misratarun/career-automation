# Career Automation System

A two-phase multi-agent system for intelligent resume optimization and job search.

## Phase 1: Intelligent Automation (Resume Optimizer)

- Reads 7 years of career documentation (DOCX files)
- Analyzes job postings (text, PDF, or URL)
- Generates ATS-optimized resume bullets
- Updates Google Doc with skill-match scoring
- Time saved: 40–50 hours manual work → 2–3 minutes per role

## Phase 2: Autonomous Career Agent (In Progress)

- Autonomous job board monitoring
- Strategic role evaluation against personal goals
- Skill gap analysis and learning path suggestions
- Interview feedback loops with continuous refinement

## Architecture

Three-agent design for Phase 1:

- **Resume Analyzer** — Extract 7-year skill and achievement patterns from DOCX files
- **Job Matcher** — Analyze posting, map requirements, score skill match %
- **Document Updater** — Update Google Doc via Google Workspace MCP

See `docs/ARCHITECTURE_DECISIONS.md` for design rationale and interview-ready explanations.

## Quick Start

```bash
# Clone repo
git clone https://github.com/misratarun/career-automation.git
cd career-automation

# Setup environment
cp config/.env.example .env
# Edit .env with your paths and credentials
bash config/setup.sh

# Run Phase 1
python phase-1/main.py - job-posting "path/to/job_posting.txt"
```

## Documentation

- `docs/CLAUDE.md` — Decision log and progress tracker
- `docs/ARCHITECTURE_DECISIONS.md` -  Why multi-agent, trade-offs, scaling to Phase 2
- `docs/DESIGN.md` — Technical specifications and pseudocode
- `docs/METRICS.md` — Performance benchmarks and results

## License

MIT
