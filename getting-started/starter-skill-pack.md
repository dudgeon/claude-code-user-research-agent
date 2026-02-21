# Starter Skill Pack: Design & Strategy

## Philosophy

The starter skill pack walks a tightrope: include enough to demonstrate the value of skills, but not so much that PMs are overwhelmed or don't feel the need to create their own.

Pre-loaded skills serve three purposes:

1. **Immediate utility**: PMs can be productive on Day 1 without understanding how skills work
2. **Pattern demonstration**: Each skill models good skill design, so PMs who want to create their own have templates to follow
3. **Research instrumentation**: The research-log skill is essential to data collection

The pack should contain 4-6 skills total. More than that creates decision paralysis and hides the mechanism.

---

## Recommended Starter Skills

### 1. research-log (Required)

**Purpose**: Generates structured session research logs for the Trailblazers program.

**File**: `.claude/skills/research-log.md`

**Notes**: This is the instrumentation skill. It's required for the pilot and is described in detail in the companion document (04-research-log-skill.md). It also serves as an example of a well-structured skill.

### 2. prd-drafter

**Purpose**: Guides Claude through drafting a product requirements document following Capital One's preferred structure.

**File**: `.claude/skills/prd-drafter.md`

**Sketch**:

```markdown
# PRD Drafter

## Trigger
When the user asks to draft, create, or write a PRD, product spec, or requirements document.

## Process

1. Before drafting, gather context by asking (if not already provided):
   - What problem does this solve and for whom?
   - What are the key constraints (timeline, technical, regulatory)?
   - What does success look like? (metrics, outcomes)
   - Who is the primary audience for this document?

2. Draft the PRD with these sections:
   - **Overview**: Problem statement, target user, and value proposition (2-3 sentences each)
   - **Goals & Success Metrics**: What we're trying to achieve and how we'll measure it
   - **User Stories / Requirements**: Structured as "As a [user], I want [action] so that [benefit]"
   - **Scope**: What's in, what's explicitly out, and known open questions
   - **Assumptions & Dependencies**: What we're assuming is true, and what we depend on
   - **Risks**: What could go wrong and proposed mitigations
   - **Timeline**: Key milestones if known

3. Save as `output/prd-[descriptive-name].md`

4. After drafting, ask: "Would you like me to review this for completeness, or refine any section?"

## Tone
Clear, direct, specific. Avoid filler language. Every sentence should carry information.
```

**Why this skill**: PRD writing is the single most common PM writing task. Having a structured skill for it shows immediate value and gives PMs a template to study.

### 3. feedback-synthesizer

**Purpose**: Takes a collection of customer feedback (pasted text, notes, survey responses) and synthesizes it into themes with supporting evidence.

**File**: `.claude/skills/feedback-synthesizer.md`

**Sketch**:

```markdown
# Feedback Synthesizer

## Trigger
When the user provides customer feedback, survey results, user research notes, or similar qualitative data and asks for synthesis, themes, or analysis.

## Process

1. Read all provided feedback carefully.

2. Identify themes using affinity grouping:
   - Group related feedback items
   - Name each theme descriptively (not generically)
   - Count how many feedback items support each theme

3. Output a structured synthesis:
   - **Theme summary table**: Theme name, frequency, sentiment (positive/negative/mixed), impact assessment
   - **For each theme**: 2-3 representative quotes or paraphrases, pattern description, potential implications
   - **Outliers**: Notable feedback that doesn't fit a theme but deserves attention
   - **Recommended actions**: 2-3 suggested next steps based on the synthesis

4. Save as `output/feedback-synthesis-[date].md`

## Guidelines
- Preserve the voice of users — don't over-sanitize quotes
- Distinguish between frequency (how often something is mentioned) and severity (how much it matters)
- Flag where themes might reflect sampling bias
```

**Why this skill**: Feedback synthesis is high-value PM work that's tedious to do manually and where AI adds clear value. It also demonstrates the agent handling unstructured input.

### 4. meeting-prep

**Purpose**: Helps PMs prepare for meetings by generating agendas, talking points, and anticipated questions.

**File**: `.claude/skills/meeting-prep.md`

**Sketch**:

```markdown
# Meeting Prep

## Trigger
When the user mentions an upcoming meeting, review, presentation, or sync and asks for preparation help.

## Process

1. Gather context:
   - What type of meeting? (standup, sprint review, stakeholder update, 1:1, design review, planning)
   - Who is the audience?
   - What's the primary objective? (decision needed, status update, alignment, brainstorm)
   - Any specific topics or concerns?

2. Generate preparation materials appropriate to the meeting type:

   **For status updates / stakeholder meetings**:
   - Structured talking points (3-5 key messages, each with supporting detail)
   - Anticipated questions and suggested responses
   - Recommended opening and closing

   **For planning / brainstorm meetings**:
   - Draft agenda with time allocations
   - Key questions to drive discussion
   - Relevant context or data to reference

   **For decision meetings**:
   - Decision framing (what specifically needs to be decided)
   - Options with pros/cons
   - Recommended approach with rationale
   - Fallback positions

3. Save as `output/meeting-prep-[brief-description].md`
```

**Why this skill**: Meeting prep is universal PM work. This skill demonstrates that agents can help with thinking and preparation, not just writing.

### 5. weekly-digest (Optional, include if 5 skills isn't too many)

**Purpose**: Generates a weekly status summary by reviewing the work done in the output directory.

**File**: `.claude/skills/weekly-digest.md`

**Sketch**:

```markdown
# Weekly Digest

## Trigger
When the user asks for a weekly summary, status update, or digest. Also useful on Friday afternoons.

## Process

1. Review files in the `output/` directory modified in the past 7 days.

2. For each file, note:
   - What type of artifact it is
   - A 1-sentence summary of its content
   - Current status (draft, final, shared)

3. Generate a weekly digest:
   - **This week's output**: Categorized list of artifacts produced
   - **Key decisions or milestones**: Anything notable from the work
   - **Carried forward**: Open items or work-in-progress
   - **Suggested focus for next week**: Based on patterns and open items

4. Save as `output/weekly-digest-[date].md`

## Note
This skill works best when the user has been saving their work to the output directory throughout the week.
```

**Why this skill**: This is a meta-skill — it shows PMs that agents can reflect on accumulated work, not just execute discrete tasks. It also incentivizes saving output to files.

---

## Skill Pack Installation

**Directory structure**:
```
project/
├── .claude/
│   ├── skills/
│   │   ├── research-log.md
│   │   ├── prd-drafter.md
│   │   ├── feedback-synthesizer.md
│   │   ├── meeting-prep.md
│   │   └── weekly-digest.md    (optional)
│   └── research-logs/          (created by research-log skill)
├── output/                      (default output directory)
└── CLAUDE.md
```

**Installation**: Copy the skill files into `.claude/skills/` during participant onboarding. Can be done via a setup script, a git clone, or manual copy.

---

## Tracking Skill Utilization

The research-log skill tracks which other skills are used in each session. Over the pilot, we want to answer:

- Which pre-loaded skills get used most frequently?
- Which are never used? Why?
- At what point do PMs start modifying pre-loaded skills?
- What custom skills do PMs create? What patterns emerge?
- Are there skills that PMs request but don't exist yet?
- Do PMs share skills with each other?

This data directly informs what the standard skill pack should contain for the organization-wide rollout. The pilot skills are a hypothesis — the data will tell us if the hypothesis is right.

---

## Skills We Deliberately Did NOT Include

And why — these are candidates for future inclusion based on pilot feedback:

- **Sprint planning**: Too team-specific; needs customization before it's useful
- **Competitive analysis**: Requires web access and external data; may hit compliance boundaries
- **Stakeholder email drafter**: Communication style is highly personal; generic version could feel wrong
- **Jira ticket writer**: Requires Jira integration that may not be available in the pilot
- **Data analysis**: Requires data access; compliance implications in a banking environment
- **Presentation builder**: Claude Code is not the ideal tool for slides (yet); could frustrate rather than help

These are worth revisiting based on what PMs ask for during the pilot.
