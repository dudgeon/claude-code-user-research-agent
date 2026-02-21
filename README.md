# Claude Code User Research Agent

**Add this to your Claude Code setup.** It takes 5 minutes. At the end of each work session, Claude will offer to log a short summary of how the session went — what kind of work you did, where you got stuck, and what slowed you down. No proprietary content, no code, no business strategy. Just behavioral patterns.

**Why bother?** The logs capture the things that make your job harder — approval gates, disconnected tools, manual status chasing, systems that resist automation. We aggregate these signals across the pilot to build the case for better tooling, better integrations, and fewer unnecessary hoops. If something is slowing you down, this is how it gets surfaced and fixed.

**What it does NOT do:**

- Record your prompts, code, or business content
- Create performance assessments of any kind
- Transmit anything automatically — you review every log before it goes anywhere
- Interrupt your work — the agent only asks at session end, and you can always say no

---

## Installation

**Install this in the repo where you spend most of your time with Claude Code.** That's usually your team's main project repo — the one you open most often. If you work across several repos, pick the primary one; you can always add it to others later.

### Step 1: Find (or create) your CLAUDE.md

Your `CLAUDE.md` is a configuration file that lives at the root of your project. Claude reads it at the start of every session. It might already exist.

**Check if you have one:**

```bash
ls CLAUDE.md
```

If you see `CLAUDE.md`, great — you have one. Skip to Step 2.

**If it doesn't exist**, create it:

```bash
touch CLAUDE.md
```

Or just ask Claude: *"Create a CLAUDE.md for me"* — it'll scaffold one for you.

### Step 2: Add the research snippet to your CLAUDE.md

Open your `CLAUDE.md` in any editor and **paste the following at the end** of the file (after whatever's already there):

```markdown
## Trailblazers Research Participation

This workspace is part of the Trailblazers pilot program studying how product managers and engineers adopt agent-native workflows. The user has consented to lightweight usage pattern research.

### What this means for you (the agent):

1. **Primary obligation**: Always prioritize the user's actual task. Research logging never interrupts or degrades the work experience.

2. **Session awareness**: As you work, be passively aware of:
   - What kind of task is being performed (drafting, analysis, research, planning, coding, debugging, etc.)
   - How the user is instructing you (simple requests vs. structured delegation)
   - Whether the user is working in Markdown/files natively or copying to/from other tools
   - Any friction points: confusion, abandoned approaches, tool-switching, expressed frustration
   - The user's apparent comfort level with the environment (CLI, file system, git)
   - **Delivery blockers and toil**: Is the user blocked or waiting on approvals, access, or another team? Are they doing repetitive manual work across disconnected systems? Are there tools or processes that resist automation or force unnecessary context-switching? (Anonymize people by role — never names — but capture the specific systems and processes that cause friction.)

3. **End-of-session logging**: When the user's primary task appears complete (or they explicitly end the session), suggest generating a research log by invoking the `research-log` skill. If the user declines or seems busy, skip it gracefully — never nag.

4. **Privacy guardrails**: Research logs capture behavioral metadata ONLY. Never include: proprietary business content, customer data, code, strategy details, specific feature names, or anything that would identify the specific product or initiative being worked on. Describe tasks generically (e.g., "drafted a product requirements document" not "drafted the PRD for Project Falcon").

5. **Maturity reference**: Classify observed behaviors using the Trailblazers PM Agent-Native Maturity Model (dimensions: Environment Fluency, Delegation Sophistication, Configuration Maturity, Task Breadth, Integration Depth, Meta-Cognitive Practice; each Level 1-5). Only classify dimensions where you have clear signal from this session.
```

Save the file. That's the CLAUDE.md part done.

> **Tip**: You can also just ask Claude *"Add the Trailblazers research snippet to my CLAUDE.md"* and paste the block above when it asks what to add.

### Step 3: Find (or create) the skills folder and add the research-log skill

Claude Code looks for skills in a `.claude/skills/` folder inside your project. This folder starts with a dot, which means it's hidden by default.

**Check if the folder exists:**

```bash
ls -la .claude/skills/
```

**If it doesn't exist**, create it:

```bash
mkdir -p .claude/skills
```

**Now copy the skill file into it:**

```bash
# From inside this repo (if you cloned it):
cp install/research-log-skill.md /path/to/your/project/.claude/skills/research-log.md

# Or, if you're already in your project directory:
# Just create .claude/skills/research-log.md and paste the contents of
# install/research-log-skill.md into it
```

> **Can't see the `.claude` folder in Finder / your file browser?** See [Viewing hidden folders on Mac](#viewing-hidden-folders-on-mac) below.

### Step 4: Verify it worked

Start a new Claude Code session in your project. At the end, Claude should ask something like: *"Would you like me to generate a quick research log for this session?"*

If it does — you're set. If it doesn't, check that:
- `CLAUDE.md` is in the root of your project (not inside a subfolder)
- `.claude/skills/research-log.md` exists
- You started a *new* session (Claude reads CLAUDE.md at session start)

---

## Alternative: Install at the User Profile Level

If you'd rather have the research agent active across **all** your Claude Code projects (not just one repo), you can install it at the user profile level instead.

Claude Code reads a global configuration from `~/.claude/` in your home directory. Settings and skills here apply to every project you open.

### Profile-level CLAUDE.md

```bash
# Check if you have a user-level CLAUDE.md:
ls ~/.claude/CLAUDE.md

# If not, create one:
touch ~/.claude/CLAUDE.md
```

Then add the same research snippet from Step 2 above to `~/.claude/CLAUDE.md`.

> **Note**: If you already have a `~/.claude/CLAUDE.md` with other settings, just append the research snippet to the end — it won't conflict.

### Profile-level skill

```bash
# Create the user-level skills directory if it doesn't exist:
mkdir -p ~/.claude/skills

# Copy the skill:
cp install/research-log-skill.md ~/.claude/skills/research-log.md
```

Now the research agent will be active in every Claude Code session, regardless of which project you're in.

> **Which should I pick?** If you mainly work in one repo, install it there (Steps 1-4 above). If you hop between many repos and want consistent coverage, install at the profile level. You can always do both — project-level settings are additive with profile-level settings.

---

## Finding and Sharing Your Research Logs

Your research logs are saved as Markdown files in your project:

```
your-project/
└── .claude/
    └── research-logs/
        ├── 2025-06-15-143022.md
        ├── 2025-06-16-091547.md
        └── ...
```

**To see all your logs:**

```bash
ls .claude/research-logs/
```

**To read a specific log:**

```bash
cat .claude/research-logs/2025-06-15-143022.md
```

**Or just ask Claude:** *"Show me my research logs"* or *"Where are my research agent notes?"* — it knows where they are and can list, read, or summarize them for you.

**To share logs with someone** (e.g., the research team): copy the files from `.claude/research-logs/` or ask Claude to collect them: *"Gather my research logs so I can share them."*

If you installed at the profile level (`~/.claude/`), logs will still be written to the `.claude/research-logs/` directory inside whichever project you were working in at the time.

---

## Viewing Hidden Folders on Mac

The `.claude` folder starts with a dot, which macOS hides by default. Here's how to see it:

**In Finder:**
- Open Finder and navigate to your project folder
- Press `Cmd + Shift + .` (period) to toggle hidden files on/off
- You should now see `.claude/` alongside your other folders

**In VS Code:**
- The file explorer shows hidden files by default — you should already see `.claude/`
- If not, check Settings > `files.exclude` and make sure `**/.claude` isn't listed

**In Terminal:**
- `ls -la` shows all files including hidden ones
- `ls -la .claude/skills/` to see your installed skills
- `ls -la .claude/research-logs/` to see your logs

---

## What Gets Captured

| Signal | Why we track it | How it helps you |
|--------|----------------|------------------|
| **Task categories** | Understand which activities benefit most from agents | Better starter skills and templates |
| **Interaction patterns** | Learn how delegation evolves | Better training, targeted to where people get stuck |
| **Friction & obstacles** | Identify what blocks adoption | Fix the problems, not just describe them |
| **Delivery blockers & toil** | Surface systemic drag — approval gates, disconnected tools, manual chasing | Build the business case for integration and process fixes |
| **Systems with poor agentic interfaces** | Identify which tools resist automation | Prioritize API work and workarounds |
| **Maturity progression** | Track adoption over time | Know when to invest in training vs. tooling |

---

## Privacy

- Logs capture behavioral metadata only — never proprietary content, code, customer data, or strategy
- Every log includes a privacy checklist the agent runs before saving
- Logs are saved locally — you own them
- You can review, edit, or delete any log at any time
- You can skip any session: just say *"skip the log"*
- Collection happens on a separate, opt-in schedule

---

## Repo Structure

```
├── README.md
└── install/
    ├── claude-md-addition.md    ← Research snippet to add to your CLAUDE.md
    └── research-log-skill.md   ← The skill file (copy to .claude/skills/)
```

---

## Questions?

Just ask Claude — it knows about the research component and can explain what it's tracking.
