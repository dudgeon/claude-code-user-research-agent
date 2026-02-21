# Trailblazers: Agent-Instrumented User Research

## Executive Summary

The Trailblazers pilot gives a small number of hand-picked product management teams access to Claude Code — Anthropic's agentic coding assistant — for a defined trial period. The pilot is small, but the findings must inform an organization-wide strategy to move hundreds of PMs toward agent-native workflows.

Traditional user research methods (surveys, interviews, observation) cannot capture how people actually adopt radically new tools. Surveys are recall-biased, interviews are expensive and slow, and observation distorts the very behavior you're trying to study.

**Our approach: use the agent itself as the research instrument.** Each pilot PM adds two lightweight components to their Claude Code setup: a brief addition to their CLAUDE.md configuration file (~15 lines) and a pre-installed research-log skill. The agent passively observes its own usage patterns during normal work, then generates a structured behavioral log at session end — capturing task types, interaction patterns, environment comfort, delegation sophistication, and maturity classification. Never proprietary content, code, or strategy.

This creates a real-time behavioral record that's richer than surveys, faster than interviews, and costs nothing in participant time. Four analysis checkpoints across 8 weeks transform raw data into a validated maturity model, training curriculum, starter kit, and scaling playbook.

The meta-argument: if we can't use an agent to study agent adoption, we've already failed to internalize the approach we're teaching.

## Repository Contents

### Presentation

`trailblazers-research-plan.pptx` — 14-slide executive deck presenting the research instrumentation plan. Structured as a narrative argument (SCQA framework) with action titles, code snippets, flow diagrams, and the maturity model. Designed for a product executive sponsor audience with limited familiarity with agent control primitives.

### Supporting Documents (01–09)

These nine documents form the complete operational toolkit for the Trailblazers research program:

| # | Document | Purpose |
|---|----------|---------|
| 01 | `01-strategic-research-brief.md` | Foundational strategy doc — research questions, methodology, success metrics, and deliverable timeline |
| 02 | `02-maturity-model.md` | PM Agent-Native Maturity Model — 6 dimensions, 5 levels each, with behavioral indicators and compact shorthand notation |
| 03 | `03-claude-md-addition.md` | The exact CLAUDE.md text participants add — ~15 lines with installation instructions and privacy guardrails |
| 04 | `04-research-log-skill.md` | The research skill file — generates structured session logs with task categories, interaction patterns, and maturity assessment |
| 05 | `05-analysis-playbook.md` | 8-week analysis roadmap — four checkpoint rounds with quantitative and qualitative methods, visualization guidance, and output templates |
| 06 | `06-participant-guide.md` | Onboarding guide for pilot PMs — what they're getting, what's expected, tips, and success criteria |
| 07 | `07-starter-claude-md-template.md` | Day 1 CLAUDE.md template — intentionally minimal to allow natural evolution (which is itself a maturity signal) |
| 08 | `08-starter-skill-pack.md` | Curated skills (PRD drafter, feedback synthesizer, meeting prep, weekly digest) with rationale for inclusions and deliberate omissions |
| 09 | `09-executive-pitch.md` | Single-page executive summary for leadership approval |

### Assets

The `/assets` folder contains reference materials used in developing the program:

- `MLA Slide Template Empty.pptx` — Capital One MLA brand slide template (Optimist font, navy brand palette) used as the design reference for the presentation
- `insight-synthesis-and-narrative-instruction.md` — Style guide for extracting insights (not summaries) and constructing presentation narratives using SCQA framework and action titles

## Key Concepts Explained

**CLAUDE.md** — A plain-text configuration file that lives in a project folder. When Claude Code opens a project, it reads this file first. It contains context about the user, their preferences, and working conventions. Think of it as a briefing document for a new colleague.

**Skills** — Reusable markdown files (stored in `.claude/skills/`) that teach the agent how to perform specific recurring tasks. Think of them as playbooks an employee pulls off the shelf. The research-log skill is what generates the structured behavioral data.

**Maturity Model** — A six-dimension framework (Environment Fluency, Delegation Sophistication, Configuration Maturity, Task Breadth, Integration Depth, Meta-Cognitive Practice) for classifying where a PM sits on their agent-native adoption journey. Each dimension has 5 levels. Encoded as compact shorthand (e.g., `E3-D2-C1-T2-I1-M2`) for tracking and comparison.

## How the Documents Connect

```
Strategic Brief (01)        ← Defines research questions and success metrics
        │
        ├── Maturity Model (02)     ← Classification framework used by everything below
        │
        ├── CLAUDE.md Addition (03) ← What participants install (data collection trigger)
        ├── Research Skill (04)     ← What generates the data (structured logs)
        │
        ├── Analysis Playbook (05)  ← How to analyze the data (4 checkpoints over 8 weeks)
        │
        ├── Participant Guide (06)  ← Onboarding for pilot PMs
        ├── Starter CLAUDE.md (07)  ← Day 1 configuration template
        ├── Starter Skill Pack (08) ← Day 1 skills (value + instrumentation)
        │
        └── Executive Pitch (09)    ← Approval request for leadership
                │
                └── Presentation (pptx) ← Visual narrative of the full plan
```

## Open Questions

These were identified in the initial planning and remain to be resolved:

1. **Log collection mechanism** — Shared git repo is ideal but may be a maturity hurdle for Day 1 PMs. Alternatives: scheduled collection script or manual upload.
2. **Compliance review** — The CLAUDE.md addition and research skill need formal signoff before deployment.
3. **SWE instrumentation** — Whether to also instrument the software engineering participants or keep research PM-focused.
4. **Deployment logistics** — Installation support, troubleshooting channel, office hours cadence.
