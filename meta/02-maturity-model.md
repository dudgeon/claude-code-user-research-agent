# PM Agent-Native Maturity Model

## Purpose

This model provides a shared vocabulary for describing where a PM is in their journey toward agent-native work. It serves three functions: (1) helping the research skill classify observed behaviors, (2) guiding training curriculum design, and (3) enabling longitudinal tracking of individual and cohort progression.

The model has five levels across six dimensions. No PM will be at the same level across all dimensions — the profile is the point, not the average.

---

## Dimensions

### 1. Environment Fluency

How comfortable is the PM working outside of Google Docs and Slack?

| Level | Label | Indicators |
|---|---|---|
| 1 | **Tourist** | Needs hand-holding to open a terminal. Copies output back to Google Docs immediately. Treats Claude Code as a weird chat window. |
| 2 | **Visitor** | Can navigate the CLI for basic tasks. Reads Markdown files but prefers to author in Docs. Understands file paths conceptually. |
| 3 | **Resident** | Authors in Markdown comfortably. Navigates project directory structures. Uses the file system as a workspace, not just output destination. |
| 4 | **Local** | Works across terminal, editor, and agent fluidly. Comfortable with git basics (status, diff, commit). Uses Markdown as primary authoring format. |
| 5 | **Native** | Terminal, git, and file-based workflows are default. Can set up and manage their own project environments. Thinks in files and repos, not documents. |

### 2. Delegation Sophistication

How effectively does the PM instruct and direct the agent?

| Level | Label | Indicators |
|---|---|---|
| 1 | **Requestor** | Simple, single-turn requests. "Write me a PRD." "Summarize this." Treats the agent like a search engine or scribe. |
| 2 | **Director** | Provides context with requests. "Write a PRD for X feature, considering Y constraint and Z audience." Follows up to refine output. |
| 3 | **Collaborator** | Multi-turn iterative work. Provides examples and anti-examples. Asks the agent to critique its own output. Structures complex tasks into steps. |
| 4 | **Architect** | Designs multi-step workflows. Creates reusable prompt structures. Uses context documents and reference materials strategically. Understands token budgets and context windows. |
| 5 | **Orchestrator** | Chains agent tasks into pipelines. Designs skills and commands for repeatable workflows. Can articulate when agent delegation is appropriate vs. when human judgment is needed. |

### 3. Configuration Maturity

How much has the PM customized their agent environment?

| Level | Label | Indicators |
|---|---|---|
| 1 | **Default** | Stock `CLAUDE.md` or none. No custom skills or commands. Uses whatever was set up for them. |
| 2 | **Personalized** | Has added personal context to `CLAUDE.md` (role, team, preferences). May have tweaked a few settings. |
| 3 | **Structured** | `CLAUDE.md` includes project context, output preferences, and workflow instructions. Has explored or adopted 1-2 skills. |
| 4 | **Configured** | Maintains a curated `CLAUDE.md` with clear sections. Uses multiple skills. Has created at least one custom command or skill. |
| 5 | **Systematic** | `CLAUDE.md` and skills are iterated on regularly. Creates and shares skills with teammates. Has a configuration philosophy — knows what belongs in `CLAUDE.md` vs. skills vs. per-session context. |

### 4. Task Breadth

What range of PM work is the PM delegating to agents?

| Level | Label | Indicators |
|---|---|---|
| 1 | **Single-use** | One task type only (usually drafting or summarization). Agent is a writing tool. |
| 2 | **Writer's room** | Multiple content types: PRDs, emails, presentations, meeting notes. But all text-generation tasks. |
| 3 | **Analyst** | Adds research and analysis tasks: competitive analysis, data interpretation, metric definition, customer feedback synthesis. |
| 4 | **Strategist** | Uses agent for reasoning tasks: prioritization frameworks, trade-off analysis, strategy development, stakeholder communication planning. |
| 5 | **Full-spectrum** | Agent is integrated into the full PM lifecycle: discovery, definition, delivery, measurement, communication, and reflection. |

### 5. Integration Depth

How connected is agent work to the PM's existing tools and team workflows?

| Level | Label | Indicators |
|---|---|---|
| 1 | **Island** | Agent work is completely disconnected from other tools. Copy-paste is the only bridge. |
| 2 | **Bridge** | Some intentional movement between agent and legacy tools. Exports agent output into Docs/Jira. Imports context from Slack/email into sessions. |
| 3 | **Connected** | Agent output feeds directly into team artifacts (e.g., Markdown specs in repos that SWEs reference). Has a workflow for moving between tools. |
| 4 | **Embedded** | Agent work is part of team rituals. Shared repos with SWEs. Agent-generated artifacts are reviewed in existing processes (PRs, design reviews). |
| 5 | **Native** | Team workflow is built around agent-augmented collaboration. PM and SWE work in shared agent-accessible environments. Legacy tools are secondary. |

### 6. Meta-Cognitive Practice

How reflective is the PM about their own AI interaction patterns?

| Level | Label | Indicators |
|---|---|---|
| 1 | **Unaware** | No reflection on interaction quality. Takes what the agent gives. Doesn't notice when sessions are unproductive. |
| 2 | **Reactive** | Notices when things go wrong (bad output, confusion) but doesn't change approach. Blames the tool. |
| 3 | **Adaptive** | Adjusts approach based on experience. Tries different prompting strategies. Starts to develop intuitions about what works. |
| 4 | **Intentional** | Has explicit mental models for what kinds of tasks/instructions produce good results. Can explain their approach to others. |
| 5 | **Generative** | Actively experiments with new patterns. Develops and tests hypotheses about agent interaction. Contributes insights back to the PM community. |

---

## Using the Model

### For Research Classification

The research skill uses these dimensions to classify observed session behavior. Each session log includes a lightweight maturity assessment based on what was observed in that session. Over time, this creates a progression timeline for each participant.

The skill does not need to classify every dimension every session — only dimensions where clear signal is present. Missing dimensions are left blank, not defaulted to Level 1.

### For Training Design

The maturity model maps directly to training modules:

- **Levels 1→2** across all dimensions: "Foundations" — Environment setup, basic delegation, first customizations
- **Levels 2→3**: "Practitioner" — Markdown fluency, iterative collaboration, task expansion, basic integration
- **Levels 3→4**: "Advanced" — Skill creation, workflow design, team integration, prompt architecture
- **Levels 4→5**: "Leader" — Systematic configuration, full-spectrum adoption, community contribution

### For Individual Feedback

PMs can receive their maturity profile as a radar chart across the six dimensions. This is not a performance evaluation — it's a growth map. Uneven profiles are normal and expected. The goal is to identify which dimensions offer the highest leverage for each individual's role and team context.

### Maturity Profile Shorthand

For quick reference in logs and analysis, a session's observed maturity can be encoded as a 6-character string: `E3-D2-C1-T2-I1-M2` (Environment 3, Delegation 2, Configuration 1, Task breadth 2, Integration 1, Meta-cognitive 2).

---

## Expected Pilot Progression

Based on typical adoption curves and the pilot structure, we'd expect:

**Week 1**: Most PMs at Levels 1-2 across most dimensions. High Environment and Delegation variance based on prior technical exposure.

**Weeks 2-3**: Environment Fluency and Delegation Sophistication advance fastest (these improve with raw usage). Configuration Maturity lags (requires intentional effort).

**Weeks 4-6**: Task Breadth expands as PMs gain confidence. Integration Depth begins to develop if team workflows support it.

**Weeks 6-8**: Meta-Cognitive Practice becomes visible. Some PMs reach Level 3-4 in their strongest dimensions. Configuration Maturity catches up for engaged participants.

The pilot will generate the actual data to validate, refine, or replace these predictions.
