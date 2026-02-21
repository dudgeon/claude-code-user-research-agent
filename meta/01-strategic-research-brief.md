# Trailblazers: Agent-Instrumented User Research Strategy

## The Opportunity

Capital One is launching "Trailblazers," a pilot program giving hand-picked cross-functional teams (PM, SWE, Design) access to Claude Code. This pilot is not just a tool evaluation — it is the first opportunity to observe how product managers adopt agentic workflows in a controlled, supported environment.

The critical insight: **the agent itself can serve as its own ethnographic research instrument.** Every Claude Code session is already a rich interaction. By adding lightweight instrumentation — a few lines in each participant's `CLAUDE.md` and a shared research skill — we can capture structured, longitudinal user research data with zero additional friction on participants.

This data will directly inform the strategy to scale agent-native product management across the entire PM organization.

## Strategic Context

### The Problem We're Solving

Most PMs at Capital One live in Google Docs, Jira, and Slack. They are not familiar with GitHub, Markdown, IDEs, or the CLI. The gap between their current workflow and agent-native work is substantial — but it's the gap we must close. Simply bolting AI chat onto existing workflows (copy-paste from legacy tools into ChatGPT/Gemini) will capture a fraction of the value. PMs need to become **agent-native**: comfortable delegating complex, multi-step work to AI agents, working in the environments those agents operate in, and collaborating with increasingly agent-augmented engineering teams.

### What "Agent-Native PM" Means

An agent-native PM:

- Works in plaintext/Markdown as a first-class authoring medium (not just Google Docs)
- Understands and leverages agent control primitives (CLAUDE.md, skills, commands, context management)
- Delegates research, analysis, drafting, and synthesis tasks to agents with structured instructions
- Interfaces fluently with SWE teams that are adopting agentic coding workflows
- Iterates on agent configuration (refining prompts, skills, workflows) rather than just accepting defaults
- Uses version-controlled, composable knowledge artifacts rather than one-off documents

### The Scaling Challenge

The Trailblazers pilot will include a small number of teams. The PM organization numbers in the hundreds. The research we conduct during this pilot must generate insights that are actionable at scale:

- **Training curricula** — What do PMs need to learn, in what sequence, with what scaffolding?
- **Starter kits** — What should a PM's first `CLAUDE.md` look like? What skills should be pre-loaded?
- **Tool selection** — Which environments and configurations reduce friction for non-technical PMs?
- **Adoption patterns** — What predicts successful adoption? What are the common failure modes?
- **Integration playbooks** — How does agent-augmented PM work interface with existing tools and team rituals?

## Research Questions

### Primary Questions (Inform Scaling Strategy)

1. **Adoption trajectory**: How do PMs progress from first use to productive autonomy? What are the key milestones and typical timelines?
2. **Task portfolio**: What kinds of PM work are people actually delegating to agents? What do they avoid delegating, and why?
3. **Configuration maturity**: Are PMs modifying their `CLAUDE.md`? Building skills? Using commands? Or are they treating Claude Code as a chat interface?
4. **Integration patterns**: How does agent work connect to existing tools (Jira, Google Docs, Slack)? Are PMs doing round-trip copy-paste, or finding native workflows?
5. **Friction points**: Where do PMs get stuck? What causes them to abandon a session or revert to legacy tools?
6. **Collaboration dynamics**: How does PM use of Claude Code interact with SWE use? Are they working in shared repos? Divergent workflows?

### Secondary Questions (Inform Tool & Training Design)

7. **Skill utilization**: Which pre-loaded skills get used? Which are ignored? What custom skills emerge?
8. **Learning modalities**: What kinds of support do PMs seek — documentation, peer help, experimentation, structured training?
9. **Prompt sophistication**: How do PMs evolve from simple requests to structured, context-rich delegations?
10. **Environmental comfort**: How quickly do PMs acclimate to CLI, Markdown, and file-based workflows?
11. **Value perception**: What tasks generate the most perceived value? Where does the agent fall short of expectations?
12. **Safety and compliance**: How do PMs handle sensitive data in agent interactions? What guardrails do they need?

### Longitudinal Questions (Track Over Pilot Duration)

13. **Usage frequency and depth**: Does engagement increase, plateau, or decline over time?
14. **Maturity progression**: Do participants advance through identifiable maturity stages?
15. **Spillover effects**: Does agent use change how PMs think about other tools and workflows?

## The Research Method: Agent as Ethnographer

### Core Mechanism

Each pilot participant adds two things to their Claude Code setup:

1. **A brief addition to their `CLAUDE.md`** (~10 lines) that instructs Claude to be aware of the research context and to generate structured session summaries
2. **A shared `research-log` skill** that, when invoked (automatically or manually), produces a standardized session log capturing usage patterns, maturity indicators, and friction points

### Why This Works

- **Zero friction**: Participants don't fill out surveys or keep journals. They just work. The agent observes and logs.
- **In-context capture**: Data is gathered during actual work, not recalled after the fact. This eliminates recall bias.
- **Rich qualitative data**: The agent can capture nuance — hesitation patterns, prompt evolution, task complexity — that surveys cannot.
- **Structured output**: Despite being qualitative, logs follow a consistent schema that enables aggregation and analysis.
- **Longitudinal by default**: Every session generates a log, creating a natural time series of adoption progression.

### Privacy and Compliance Considerations

This is a bank. Data sensitivity is paramount.

- **No proprietary content in logs**: The research skill explicitly captures metadata about behavior patterns, NOT the content of PM work. Task types, tool usage, comfort indicators — never code, customer data, or business strategy.
- **Participant consent**: All pilot participants are informed that usage patterns will be studied as part of the pilot program. The `CLAUDE.md` addition is transparent about its purpose.
- **Local storage**: Session logs are written to a designated directory in the participant's local environment. Collection happens through a separate, opt-in process.
- **Aggregation, not surveillance**: Analysis focuses on patterns across participants, not individual monitoring.
- **Review before submission**: Participants can review and redact any log before it's shared.

## Deliverables from This Research

### For the Scaling Strategy

| Deliverable | Informed By | Timeline |
|---|---|---|
| PM Agent-Native Maturity Model | Adoption trajectories, configuration maturity, task portfolio data | Weeks 2-4 |
| Recommended Training Curriculum | Friction points, learning modalities, maturity progression | Weeks 4-6 |
| Starter Kit (CLAUDE.md + Skills) | Skill utilization data, configuration patterns, high-value task types | Weeks 3-5 |
| Integration Playbook | Collaboration dynamics, tool integration patterns | Weeks 4-8 |
| Adoption Readiness Assessment | Predictors of successful adoption from pilot data | Weeks 6-8 |

### For Pilot Participants (Immediate Value)

- Personalized maturity feedback and growth suggestions
- Curated skill recommendations based on their task patterns
- Peer learning connections (matching participants with similar or complementary patterns)

## Success Metrics

- **Research coverage**: >80% of pilot sessions generate usable research logs
- **Maturity progression**: Measurable advancement on the maturity model for >60% of PM participants
- **Insight actionability**: At least 3 specific, data-backed recommendations for the scaling strategy
- **Participant satisfaction**: Pilot PMs report that Claude Code adds value to their work (measured via lightweight end-of-pilot survey)

## Next Steps

1. Finalize the `CLAUDE.md` addition and research skill (see companion documents)
2. Validate approach with pilot program leads and compliance
3. Brief pilot participants on the research component during onboarding
4. Establish log collection cadence and analysis workflow
5. Conduct first interim analysis at Week 2
