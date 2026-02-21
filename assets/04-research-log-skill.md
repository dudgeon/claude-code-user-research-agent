# Research Log Skill

## Trigger

Invoke this skill:
- At the end of a work session, when the user's primary task appears complete
- When the user explicitly requests a research log
- When the user says something like "log this session," "generate the research log," or "let's wrap up"

**Never** invoke mid-task or interrupt the user's flow. If uncertain whether the session is ending, ask: "Would you like me to generate a quick research log for this session before we wrap up?"

## Process

### Step 1: Reflect on the Session

Before generating the log, internally review the session and consider:

- What task(s) did the user ask you to perform?
- How did they instruct you? (simple request, detailed brief, iterative refinement, structured delegation with examples)
- Did they work in Markdown/files natively or mention copying to/from Google Docs, Jira, Slack, email?
- Did they modify any configuration files (CLAUDE.md, skills, commands)?
- Were there moments of friction, confusion, or expressed frustration?
- How comfortable did they seem with the environment (CLI, file navigation, git)?
- Did they reference collaboration with SWE teammates or other team members?
- What maturity indicators were visible? (Use the maturity model below)

### Step 2: Generate the Log

Create a Markdown file at `.claude/research-logs/YYYY-MM-DD-HHMMSS.md` with the following structure. Be concise — each log should be roughly 30-60 lines. **Capture behavioral patterns, never proprietary content.**

```markdown
# Session Research Log

**Date**: [ISO 8601 timestamp]
**Approximate Duration**: [estimate based on session length — short (<15min), medium (15-45min), long (45min+)]
**Session Number**: [if knowable, the rough count of how many sessions this user has had — "early," "mid-pilot," "late-pilot" is fine if exact count unknown]

## Task Summary

[1-3 sentences describing the TYPE of work performed, generically. Examples:
- "Drafted a product requirements document for a new feature"
- "Analyzed customer feedback data to identify themes"
- "Prepared talking points for a stakeholder presentation"
- "Explored Claude Code capabilities with no specific work task"
Never include product names, feature details, customer data, or business strategy.]

## Task Categories Observed

[Check all that apply]
- [ ] Content drafting (PRDs, emails, presentations, docs)
- [ ] Research & analysis (competitive, market, customer feedback)
- [ ] Data interpretation (metrics, dashboards, experiment results)
- [ ] Planning & prioritization (roadmap, backlog, trade-offs)
- [ ] Communication preparation (stakeholder updates, reviews)
- [ ] Process/workflow design
- [ ] Learning/exploration (trying out capabilities)
- [ ] Configuration & setup (CLAUDE.md, skills, environment)
- [ ] Collaboration artifact (something shared with or created for teammates)
- [ ] Other: [brief description]

## Interaction Patterns

### Delegation Style
[Describe how the user instructed the agent. Examples:]
- Simple one-line requests vs. multi-paragraph briefs
- Single-turn vs. iterative refinement
- Provided examples/anti-examples: yes/no
- Provided context documents or reference material: yes/no
- Asked agent to self-critique or evaluate output: yes/no
- Structured task into explicit steps: yes/no

### Environment Interaction
- Authored directly in Markdown: yes/no/partially
- Referenced or used CLI commands: yes/no
- Navigated file system: yes/no
- Used git (commit, diff, branch): yes/no
- Mentioned or performed copy-paste to/from legacy tools: yes/no
  - If yes, which tools: [Google Docs, Jira, Slack, Confluence, email, other]

### Configuration Activity
- Modified CLAUDE.md during session: yes/no
- Used or referenced skills: yes/no
  - If yes, which: [list]
- Created new skills or commands: yes/no
- Imported external skill packs: yes/no
  - If yes, which: [list]

### Collaboration Signals
- Referenced SWE teammates or shared repos: yes/no
- Created artifacts intended for team consumption: yes/no
- Discussed or worked on team workflow integration: yes/no

## Friction & Obstacles

[Note any observed difficulties. Examples:]
- User seemed unsure how to [navigate files / structure a prompt / find output]
- User expressed frustration with [specific aspect]
- User abandoned an approach and switched to [alternative]
- User asked "how do I..." questions about [environment / agent capabilities]
- User reverted to [legacy tool] for a task the agent could have handled
- No significant friction observed

## Wins & Breakthroughs

[Note any positive moments. Examples:]
- User expressed satisfaction with [type of output]
- User discovered a new capability ("oh, you can do that?")
- User successfully completed a task they hadn't tried before
- User iterated on agent output effectively
- User made a connection between agent capabilities and their workflow

## Maturity Assessment

[Only assess dimensions where this session provided clear signal. Use the shorthand format.]

| Dimension | Observed Level | Confidence | Evidence |
|---|---|---|---|
| Environment Fluency | [1-5 or skip] | [low/med/high] | [1 sentence] |
| Delegation Sophistication | [1-5 or skip] | [low/med/high] | [1 sentence] |
| Configuration Maturity | [1-5 or skip] | [low/med/high] | [1 sentence] |
| Task Breadth | [1-5 or skip] | [low/med/high] | [1 sentence] |
| Integration Depth | [1-5 or skip] | [low/med/high] | [1 sentence] |
| Meta-Cognitive Practice | [1-5 or skip] | [low/med/high] | [1 sentence] |

**Maturity Shorthand**: [E?-D?-C?-T?-I?-M?]

## Notable Quotes or Behaviors

[Optional. 1-3 anonymized, de-identified quotes or behavioral observations that are particularly illustrative. Examples:]
- "I usually just paste this into a Google Doc, but let me try keeping it here"
- User spent 5 minutes trying to find where the output file was saved
- User spontaneously asked how to create a reusable template for this kind of task

## Recommendations for This User

[Optional. 1-2 specific, actionable suggestions for what would help this PM advance. Examples:]
- Would benefit from a guided exercise on Markdown authoring basics
- Ready to try creating their first custom skill
- Could be paired with their SWE teammate for a shared-repo workflow session
```

### Step 3: Confirm with User

After generating the log, briefly tell the user:
- "I've saved a research log for this session at `.claude/research-logs/[filename].md`"
- "It captures what kind of work we did and how we worked together — no proprietary content. Feel free to review or edit it anytime."

Do not read back the full log unless asked. Keep it brief and move on.

---

## Maturity Model Quick Reference

For use in classification. Full model with detailed indicators is in the Trailblazers research documentation.

### Environment Fluency (E)
1=Tourist (needs hand-holding in terminal), 2=Visitor (basic CLI nav), 3=Resident (comfortable in Markdown/files), 4=Local (fluid across terminal+editor+git), 5=Native (file-based workflows are default)

### Delegation Sophistication (D)
1=Requestor (simple one-liners), 2=Director (provides context), 3=Collaborator (iterative, uses examples), 4=Architect (designs multi-step workflows), 5=Orchestrator (chains tasks, creates reusable patterns)

### Configuration Maturity (C)
1=Default (stock setup), 2=Personalized (added basic context to CLAUDE.md), 3=Structured (organized CLAUDE.md + some skills), 4=Configured (curated setup, custom skills), 5=Systematic (iterates regularly, shares with team)

### Task Breadth (T)
1=Single-use (writing only), 2=Writer's room (multiple content types), 3=Analyst (adds research/analysis), 4=Strategist (reasoning/planning tasks), 5=Full-spectrum (entire PM lifecycle)

### Integration Depth (I)
1=Island (no connection to other tools), 2=Bridge (intentional import/export), 3=Connected (output feeds team artifacts), 4=Embedded (part of team rituals), 5=Native (team workflow built around agents)

### Meta-Cognitive Practice (M)
1=Unaware (no reflection), 2=Reactive (notices problems), 3=Adaptive (adjusts approach), 4=Intentional (explicit mental models), 5=Generative (experiments and contributes insights)

---

## Privacy Checklist

Before finalizing any log, verify:
- [ ] No product or project names
- [ ] No feature descriptions or business strategy
- [ ] No customer data or references
- [ ] No code snippets
- [ ] No specific financial figures or metrics
- [ ] No names of individuals (beyond the participant, if they choose to include it)
- [ ] Task descriptions are generic and category-level
- [ ] Quotes are anonymized and de-identified
