# Claude Code User Research Agent

Thank you for your interest in helping us learn about how Claude Code is being used in the organization — your participation will give us better insight into the tools, training, and resources that will help you and users like you the most. Here's how to help:

**Make two tiny changes to your Claude Code setup.** It takes less than 2 minutes. At the end of each work session, Claude will offer to log a short summary of how the session went — what kind of work you did, where you got stuck, and what slowed you down. No proprietary content, no code, no business strategy. Just behavioral patterns.

**Why bother?** The logs capture the things that make your job harder — approval gates, disconnected tools, manual status chasing, systems that resist automation. We aggregate these signals across the pilot to build the case for better tooling, better integrations, and fewer unnecessary hoops. If something is slowing you down, this is how it gets surfaced and fixed.

**What it does NOT do:**

- Record your prompts, code, or business content
- Create performance assessments of any kind
- Transmit anything automatically — you review every log before it goes anywhere
- Interrupt your work — the agent only asks at session end, and you can always say no

<p align="center">
  <img src="assets/panel-1-welcome.png" width="48%" alt="A friendly research robot arrives at a PM's desk" />
  <img src="assets/panel-2-observing.png" width="48%" alt="The robot quietly observes from a shelf while the PM works" />
</p>
<p align="center">
  <img src="assets/panel-3-notes.png" width="48%" alt="The robot fills its notebook with observations" />
  <img src="assets/panel-4-goodbye.png" width="48%" alt="End of day — the robot departs with a full notebook" />
</p>

---

## Installation

**Install this in the repo where you spend most of your time with Claude Code.** That's usually your team's main project repo — the one you open most often. If you work across several repos, pick the primary one; you can always add it to others later.

### Step 1: Find (or create) your CLAUDE.md

Your `CLAUDE.md` is a configuration file that lives at the top level of your project folder. Claude reads it at the start of every session. It might already exist.

**Check if you have one:** In VS Code, look in the file explorer sidebar (the left panel) for a file called `CLAUDE.md` at the top of your project. You can also open your project folder in Finder and look for it there.

If you see `CLAUDE.md`, great — you already have one. Skip to Step 2.

**If it doesn't exist**, the easiest way to create one is to open Claude Code and ask: *"Create a CLAUDE.md for me."*

### Step 2: Add the research snippet to your CLAUDE.md

Open [`claude-md-addition.md`](claude-md-addition.md) in this repo, select all, copy, and **paste it at the end** of your `CLAUDE.md` (after whatever's already there). Save the file.

> **Tip**: You can also ask Claude *"Add the research snippet to my CLAUDE.md"* and paste the contents of `claude-md-addition.md` when it asks what to add.

### Step 3: Add the research-log skill

Claude Code looks for skills in a folder called `.claude/skills/` inside your project. You need to put one file there.

**The easiest way:** Open Claude Code in your project and say:

*"Create a file at `.claude/skills/research-log.md`"*

Then paste the entire contents of [`research-log-skill.md`](research-log-skill.md) from this repo when Claude asks what to put in it.

**Or do it by hand:** In VS Code, look for a `.claude` folder in your project's sidebar. If you don't see it, you may need to show hidden files (see [Viewing hidden folders](#viewing-hidden-folders) below). Create a `skills` folder inside `.claude`, then create a file called `research-log.md` inside that and paste the contents of [`research-log-skill.md`](research-log-skill.md).

### That's it — verify it worked

Start a **new** Claude Code session in your project. At the end, Claude should offer something like: *"Would you like me to generate a quick research log for this session?"*

If it does — you're set. If it doesn't, check that:

- `CLAUDE.md` is at the top level of your project (not inside a subfolder)
- The file `.claude/skills/research-log.md` exists
- You started a *new* session (Claude reads CLAUDE.md at session start)

---

## Finding and Sharing Your Research Logs

Your research logs are saved inside your project at `.claude/research-logs/`. Each session gets its own file.

**The easiest way to find them:** Just ask Claude — *"Show me my research logs"* or *"Where are my research agent notes?"* It knows where they are and can list, read, or summarize them for you.

**To share logs** (e.g., with the research team): Ask Claude *"Gather my research logs so I can share them"* and it will collect them for you. Or copy the files directly from the `.claude/research-logs/` folder in your project.

You always own your logs. Review, edit, or delete any of them at any time.

---

## Viewing Hidden Folders

The `.claude` folder starts with a dot, which means your computer hides it by default.

**In VS Code:** The file explorer usually shows hidden files already — look for `.claude/` in the sidebar. If you don't see it, check Settings > `files.exclude` and make sure `**/.claude` isn't listed.

**In Finder (Mac):** Open your project folder and press `Cmd + Shift + .` (period) to toggle hidden files on and off.

---

## What Gets Captured

| Signal | Why we track it | How it helps you |
|--------|----------------|------------------|
| **Task categories** | Understand which activities benefit most from agents | Better starter skills and templates |
| **Lifecycle phase** | Learn where in the development process agents add value | Target investment to the right phases |
| **Interaction patterns** | Learn how delegation evolves | Better training, targeted to where people get stuck |
| **Friction & obstacles** | Identify what blocks adoption | Fix the problems, not just describe them |
| **Delivery blockers & toil** | Surface systemic drag — approval gates, disconnected tools, manual chasing | Build the business case for integration and process fixes |
| **Systems with poor agentic interfaces** | Identify which tools resist automation | Prioritize API work and workarounds |

---

## Privacy

- Logs capture behavioral metadata only — never proprietary content, code, customer data, or strategy
- Every log includes a privacy checklist the agent runs before saving
- Logs are saved locally — you own them
- You can review, edit, or delete any log at any time
- You can skip any session: just say *"skip the log"*
- Collection happens on a separate, opt-in schedule

---

## Questions?

Just ask Claude — it knows about the research component and can explain what it's tracking.
