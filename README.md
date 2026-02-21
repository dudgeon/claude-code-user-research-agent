# Trailblazers Research Kit

**What this is**: A lightweight add-on for Claude Code that helps us understand what's working, what's not, and what's getting in your way — so we can fix it.

**Who this is for**: Any SWE or PM on a Trailblazers pilot team.

**What it does**: Adds a small research snippet to your `CLAUDE.md` and a `research-log` skill. At the end of a work session, the agent offers to generate a short, structured log capturing:

- What *kind* of work you did (categories, never content)
- How you and the agent worked together
- Where you got stuck — friction, blockers, toil
- Which tools and systems added drag to your delivery

**Why this helps you specifically**: The logs capture the things that slow you down — the approval gates, the disconnected systems, the manual copy-paste between tools, the places where you're waiting on status from something that should just tell you. We aggregate these signals to build the case for better tooling, better integrations, and fewer unnecessary hoops. If a system is making your life harder, this is how it gets surfaced.

**What it does NOT do**:

- Record your prompts, code, business strategy, or proprietary content
- Create individual performance assessments
- Transmit anything automatically — you review every log before it goes anywhere
- Interrupt your work — the agent only asks at session end, and you can always skip it

---

## Quick Start (5 minutes)

### 1. Copy the research-log skill into your project

```bash
mkdir -p .claude/skills
cp install/04-research-log-skill.md .claude/skills/research-log.md
```

### 2. Add the research snippet to your CLAUDE.md

If you already have a `CLAUDE.md`, append the "Trailblazers Research Participation" section from [`install/03-claude-md-addition.md`](install/03-claude-md-addition.md) to the end of your file.

If you don't have a `CLAUDE.md` yet, use the starter template:

```bash
cp install/07-starter-claude-md-template.md CLAUDE.md
```

Then fill in the `About Me` and `How I Work` sections.

### 3. (Optional) Install the starter skill pack

The skill pack includes useful everyday skills (PRD drafter, feedback synthesizer, meeting prep, weekly digest) described in [`install/08-starter-skill-pack.md`](install/08-starter-skill-pack.md). Copy whichever ones look useful into `.claude/skills/`.

### 4. Work normally

That's it. The agent will ask at the end of a session if you want to generate a research log. Say yes or no — it won't nag.

---

## What Gets Captured (and Why It Matters)

| Signal | Why we track it | How it helps you |
|--------|----------------|------------------|
| **Task categories** | Understand which PM activities benefit most from agents | Better starter skills and templates for your workflow |
| **Interaction patterns** | Learn how delegation sophistication evolves | Better training materials, targeted to where people actually get stuck |
| **Friction & obstacles** | Identify what blocks adoption | Fix the problems, not just describe them |
| **Delivery blockers & toil** | Surface systemic drag — approval gates, disconnected tools, manual status chasing | Build the business case for integration, automation, and process fixes |
| **Systems with poor agentic interfaces** | Identify which tools resist automation | Prioritize API work, integrations, and workarounds |
| **Maturity progression** | Track adoption across the cohort over time | Know when and where to invest in training vs. tooling |

### On Blockers and Toil

This is new. Beyond observing how you use the agent, the research-log now captures delivery friction:

- **Blockers**: Waiting for approvals, access, other teams' deliverables, broken environments
- **Toil**: Manual status updates across systems, copy-pasting between tools, reformatting the same content for different audiences, chasing people for information
- **Poor agentic interfaces**: Systems with no API, tools that force you into a browser to get a single piece of data, notifications that lack context

We anonymize everything — "manager" not a name, "ticketing system" not necessarily the specific product. But we do capture the *specific shape of the friction*: which systems, which handoffs, which processes. That specificity is what turns a vague "things are slow" into an actionable improvement backlog.

---

## Repo Structure

```
├── README.md              ← You are here
├── install/               ← Files you actually install
│   ├── 03-claude-md-addition.md    ← Snippet to add to your CLAUDE.md
│   ├── 04-research-log-skill.md    ← The research-log skill (copy to .claude/skills/)
│   ├── 07-starter-claude-md-template.md  ← Full starter CLAUDE.md if you need one
│   └── 08-starter-skill-pack.md    ← Optional additional skills
│
└── meta/                  ← Research strategy & planning (you don't need these)
    ├── research-context.md         ← Project background and original prompt
    ├── 01-strategic-research-brief.md  ← Research questions and methodology
    ├── 02-maturity-model.md        ← The 6-dimension maturity framework
    ├── 05-analysis-playbook.md     ← How we analyze the collected data
    ├── 06-participant-guide.md     ← Onboarding guide for pilot PMs
    └── 09-executive-pitch.md       ← Leadership approval document
```

The `install/` folder has everything you need. The `meta/` folder is for the research team — strategy docs, analysis playbooks, and stakeholder communications. You're welcome to read them, but you don't need to.

---

## Privacy

- Logs capture behavioral metadata only — never proprietary content, code, customer data, or strategy details
- Every log includes a privacy checklist the agent runs before saving
- Logs are saved locally to `.claude/research-logs/` in your project — you own them
- You can review, edit, or delete any log at any time
- You can skip logging any session by saying "skip the log"
- Collection happens on a separate, opt-in schedule

---

## Questions?

Ask in the Trailblazers Slack channel or bring them to office hours. Or just ask Claude — it knows about the research component and can explain what it's tracking.
