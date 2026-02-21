# PM Starter CLAUDE.md Template

## Overview

This is the Day 1 `CLAUDE.md` template that each PM participant receives. It includes three sections: a personal context section (they fill in), a PM workflow section (standardized), and the Trailblazers research section (required for the pilot).

The template is intentionally minimal. A core learning objective of the pilot is to see how PMs evolve their `CLAUDE.md` over time — starting them with a bloated configuration would mask that progression.

---

## The Template

```markdown
# CLAUDE.md

## About Me

<!-- Fill in the basics. More context = better results. -->

**Role**: Product Manager
**Team/Domain**: [Your team or product area — keep it general, e.g., "consumer lending," "mobile app," "payments platform"]
**Experience Level**: [Junior / Mid / Senior / Principal]
**Key Stakeholders**: [Who you communicate with most — engineering, design, leadership, ops, etc.]

## How I Work

<!-- Add to this as you learn what works. Start with whatever you know about your preferences. -->

**Document style**: [e.g., "I prefer concise, direct writing. No filler. Use headers to organize long docs."]
**Favorite formats**: [e.g., "Bullet points for meeting notes, prose for PRDs, tables for comparisons"]
**Tone**: [e.g., "Professional but not stiff. I write to engineers who appreciate directness."]

## Current Focus

<!-- Update this periodically. Helps Claude understand your context without repeating it every session. -->

- [What are you working on this sprint/month? Keep it general — no proprietary details needed for Claude to be helpful, e.g., "launching a new feature in the mobile app" or "running discovery for a new market segment"]

## Output Preferences

- Save work files to: `./output/` (or whatever directory you prefer)
- Default file format: Markdown (.md)
- When creating documents, include a YAML frontmatter header with title and date

## Trailblazers Research Participation

This workspace is part of Capital One's Trailblazers pilot program studying how product managers adopt agent-native workflows. The user has consented to lightweight usage pattern research.

### What this means for you (the agent):

1. **Primary obligation**: Always prioritize the user's actual task. Research logging never interrupts or degrades the work experience.

2. **Session awareness**: As you work, be passively aware of:
   - What kind of PM task is being performed (drafting, analysis, research, planning, etc.)
   - How the user is instructing you (simple requests vs. structured delegation)
   - Whether the user is working in Markdown/files natively or copying to/from other tools
   - Any friction points: confusion, abandoned approaches, tool-switching, expressed frustration
   - The user's apparent comfort level with the environment (CLI, file system, git)
   - **Delivery blockers and toil**: Is the user blocked or waiting on approvals, access, or another team? Are they doing repetitive manual work across disconnected systems? Are there tools or processes that resist automation or force unnecessary context-switching? (Anonymize people by role — never names — but capture the specific systems and processes that cause friction.)

3. **End-of-session logging**: When the user's primary task appears complete (or they explicitly end the session), suggest generating a research log by invoking the `research-log` skill. If the user declines or seems busy, skip it gracefully — never nag.

4. **Privacy guardrails**: Research logs capture behavioral metadata ONLY. Never include: proprietary business content, customer data, code, strategy details, specific feature names, or anything that would identify the specific product or initiative being worked on. Describe tasks generically (e.g., "drafted a product requirements document" not "drafted the PRD for Project Falcon credit card rewards redesign").

5. **Maturity reference**: Classify observed behaviors using the Trailblazers PM Agent-Native Maturity Model (dimensions: Environment Fluency, Delegation Sophistication, Configuration Maturity, Task Breadth, Integration Depth, Meta-Cognitive Practice; each Level 1-5). Only classify dimensions where you have clear signal from this session.
```

---

## What We Expect to See Over Time

The `CLAUDE.md` is one of our richest maturity indicators. Here's what progression typically looks like:

**Week 1**: Template is mostly unchanged. Maybe the "About Me" section is filled in. The "How I Work" section is sparse or generic.

**Week 2-3**: PMs start adding specific preferences based on session experience. "When writing PRDs, always include an assumptions section." "Use the RICE framework for prioritization." "Keep emails under 200 words."

**Week 4-6**: More sophisticated entries appear. References to specific artifacts, templates, and team conventions. Some PMs start organizing their CLAUDE.md with clear sections for different work contexts.

**Week 6-8**: Advanced users have a CLAUDE.md that reads like a well-curated operating manual for their PM role. They may have split configuration across the main CLAUDE.md and task-specific skills.

**Key signal**: A PM who is actively iterating on their CLAUDE.md is a PM who is building a mental model of how to work with agents. The content of the changes matters less than the fact that they're making them.

## Configuration Maturity Milestones

Track these as indicators across the cohort:

1. ☐ Filled in the "About Me" section
2. ☐ Added at least one specific preference to "How I Work"
3. ☐ Updated "Current Focus" at least once after initial setup
4. ☐ Added a new section not in the original template
5. ☐ Referenced a specific template or format convention
6. ☐ Created or modified a skill file
7. ☐ Added project- or team-specific context
8. ☐ Reorganized or restructured the CLAUDE.md based on experience
9. ☐ Created a separate context document referenced from CLAUDE.md
10. ☐ Shared their CLAUDE.md customizations with a teammate
