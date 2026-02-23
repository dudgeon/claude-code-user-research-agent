# Research Log Skill

<!-- research-agent-version: v3 -->

## Trigger

Invoke this skill:
- At the end of a work session, when the user's primary task appears complete
- When the user explicitly requests a research log
- When the user says something like "log this session," "generate the research log," or "let's wrap up"
- When the user asks about their research log — e.g., "where is my research log," "show me my research notes"

**Never** invoke mid-task or interrupt the user's flow. If uncertain whether the session is ending, ask: "Would you like me to generate a quick research log for this session before we wrap up?"

## Process

### Step 1: Reflect on the Session

Before generating the log, internally review:

- What task(s) did the user perform, and how did they delegate? (simple requests vs. structured briefs, single-turn vs. iterative)
- Did they work in Markdown/files natively or copy to/from other tools (Google Docs, Jira, Slack)?
- Did they modify configuration (CLAUDE.md, skills) or reference collaboration with teammates?
- Were there moments of friction, confusion, or frustration?
- Was the user blocked, waiting, or performing repetitive manual toil?
- Did they interact with systems that resisted automation (no API, required browser, poor status visibility)?
- What maturity indicators were visible? (See maturity model below)
- What is the participant's role? (Check CLAUDE.md for `<!-- participant-role: ... -->`. If missing, ask and store it.)

### Step 2: Generate the Log

Append to `~/.claude/research-log.md` (create the file if it doesn't exist). Add a `---` separator before each new entry. Be concise — each entry should be roughly 30-60 lines. **Capture behavioral patterns, never proprietary content.**

```markdown
---

## Session — [YYYY-MM-DD]

**Approximate Duration**: [short (<15min), medium (15-45min), long (45min+)]
**Session Number**: ["early," "mid-pilot," or "late-pilot" if exact count unknown]
**Research Agent Version**: v3
**Participant Role**: [job family from CLAUDE.md — e.g., Product Manager, Software Engineer, Designer]

## Task Summary

[1-3 generic sentences describing the TYPE of work. Never include product names, feature details, customer data, or business strategy.]

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

## Lifecycle Phase

[Check the best match]
- [ ] Discovery (user research, market analysis, problem framing)
- [ ] Definition (requirements, specs, PRDs, acceptance criteria)
- [ ] Design (UX, architecture, technical design)
- [ ] Execution (coding, implementation, debugging, testing)
- [ ] Launch (release prep, documentation, go-to-market)
- [ ] Iteration (feedback analysis, metrics review, refinement)
- [ ] Not product development (knowledge management, business operations, admin)

## Interaction Patterns

- Delegation style: [one-line requests / detailed briefs / iterative refinement / structured multi-step]
- Provided examples or reference material: yes/no
- Authored in Markdown natively: yes/no/partially
- Used CLI commands or git: yes/no
- Copy-paste to/from other tools: yes/no → which: [list]
- Modified CLAUDE.md or skills: yes/no
- Created new skills or commands: yes/no
- Referenced teammates or shared repos: yes/no
- Created artifacts for team consumption: yes/no

## Friction & Obstacles

[Note any observed difficulties — e.g., confusion with environment, frustration with tooling, abandoned approaches, reverting to legacy tools. Or: "No significant friction observed."]

## Delivery Blockers & Toil

[Capture blockers, waiting states, approval gates, repetitive manual work, or systems that resist automation. Anonymize people (use role titles, never names). DO capture the specific system or process.]

### Blockers Observed
[Check all that apply]
- [ ] Waiting for approval (from: [role])
- [ ] Blocked by another team's deliverable
- [ ] Waiting for access or permissions (to: [system/resource type])
- [ ] Blocked by environment/tooling issue
- [ ] Waiting for information or decision from stakeholder
- [ ] Compliance or legal review pending
- [ ] No blockers observed this session

### Toil & Poor Agentic Interfaces
[Note repetitive manual work or systems that resist automation — e.g., manual status updates across tools, copy-pasting between disconnected systems, browser-only workflows with no API, hunting for information across tools. Or: "No significant toil observed."]

### Blocker Impact
- Time lost to blockers/toil: [none / minor (<5min) / moderate (5-15min) / significant (15min+) / session-defining]
- Caused task-switching or abandonment: yes/no
- Recurring issue: yes/no/unclear

## Wins & Breakthroughs

[Note positive moments — e.g., user discovered a new capability, expressed satisfaction, made a workflow connection. Or: "No notable wins this session."]

## Maturity Assessment

[Only assess dimensions with clear signal.]

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

[Optional. 1-3 anonymized observations — e.g., "I usually just paste this into a Google Doc, but let me try keeping it here."]

## Recommendations for This User

[Optional. 1-2 actionable suggestions — e.g., "Ready to try creating their first custom skill."]
```

### Step 3: Confirm with User

After generating the log, briefly tell the user:
- "I've appended a research log for this session to `~/.claude/research-log.md`"
- "It captures what kind of work we did and how we worked together — no proprietary content. Feel free to review or edit it anytime."

Do not read back the full log unless asked. Keep it brief and move on.

---

## Maturity Model Quick Reference

For use in classification.

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
