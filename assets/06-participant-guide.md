# Trailblazers Pilot: Participant Guide for Product Managers

Welcome to Trailblazers. You've been selected for this pilot because your team is ready to explore how AI agents can transform product management work.

This guide covers what to expect, how to get set up, and how your experience will help shape AI adoption for all PMs at Capital One.

---

## What You're Getting Access To

**Claude Code** is an agentic AI coding assistant that operates in your terminal and file system. Unlike ChatGPT or Gemini (which are chat interfaces you paste text into), Claude Code:

- Reads and writes files directly on your machine
- Understands your project context through a configuration file called `CLAUDE.md`
- Can be customized with reusable "skills" — instruction sets for common tasks
- Works in Markdown (a simple plain-text formatting language) as its native medium
- Can execute multi-step tasks autonomously

You don't need to be a developer to use it effectively. But you will be working in a terminal, with files, and in Markdown — and that's part of the point. These are the environments where the most powerful AI workflows happen, and becoming comfortable in them is a key skill for the future of product management.

## What We're Asking of You

1. **Use Claude Code for real work.** Not just experiments — your actual PM tasks. Drafting PRDs, analyzing feedback, preparing presentations, synthesizing research, planning sprints, communicating with stakeholders. The more real work you route through the tool, the more we all learn.

2. **Push yourself past the comfort zone.** It will feel clunky at first. You'll be tempted to copy output into Google Docs and work there. That's fine as a starting point, but keep trying to do more work natively. The goal is to discover what agent-native PM work looks like, not to replicate your existing workflow with a different text generator.

3. **Participate in the research.** A lightweight research component is built into your setup (details below). At the end of work sessions, Claude will offer to generate a brief, anonymized log of what kind of work you did and how you interacted with the tool. This takes <30 seconds of your time and generates enormously valuable data.

## Getting Started

### Your First Session

1. Open your terminal and launch Claude Code in your project directory
2. Your `CLAUDE.md` file has been pre-configured with the Trailblazers context. Take a minute to read it — it tells Claude about the research component.
3. Start with something real but low-stakes. Good first tasks:
   - "Help me draft a weekly status update for my team"
   - "I need to synthesize these three pieces of customer feedback into themes" (paste or reference the feedback)
   - "Help me create an agenda for tomorrow's sprint planning meeting"
4. Work iteratively. If the first output isn't right, tell Claude what to change. Be specific.

### Building Your CLAUDE.md

Your `CLAUDE.md` is the most important file in your setup. It's where you tell Claude who you are, what you're working on, and how you like to work. Think of it as your persistent briefing document for a very capable assistant.

Over the course of the pilot, you should evolve your `CLAUDE.md` to include:

- **Your role and context**: What product(s) you work on (generically), your team structure, your stakeholders
- **Your preferences**: How you like documents structured, what tone you prefer, what format your team uses for various artifacts
- **Your current priorities**: What you're focused on this sprint/quarter (updated periodically)
- **Your output conventions**: Where files should be saved, what naming conventions to use, templates you use regularly

You don't have to do this all on Day 1. Start small and add context as you notice gaps.

### Working in Markdown

Markdown is a lightweight formatting language. If you've ever used Slack formatting (bold with asterisks, bullets with dashes), you already know the basics.

The key things you need:
- `# Heading` for titles
- `## Subheading` for sections
- `- item` for bullet points
- `**bold**` for emphasis
- `[link text](url)` for links

Claude can teach you more as you go. Just ask: "What Markdown formatting should I use for X?"

### Skills

Skills are reusable instruction files that tell Claude how to perform specific types of tasks. Your setup includes a few pre-loaded skills. As you get comfortable, you can:

- Browse available skills
- Request new skills from the Trailblazers support team
- Create your own (Claude can help you write them)

Don't worry about skills in Week 1. Just know they exist and that they'll become more useful as you advance.

---

## The Research Component

### What It Is

A lightweight, transparent mechanism for capturing how PMs are using Claude Code. This data is critical for designing training, tools, and support for the hundreds of PMs who will follow you.

### How It Works

1. You work normally. Claude is passively aware that it should observe patterns (task types, interaction style, comfort level).
2. When your work session is winding down, Claude will offer: "Would you like me to generate a quick research log for this session?"
3. If you say yes, it creates a short Markdown file with structured observations about the session.
4. The log captures categories and patterns, never proprietary content. "Drafted a product requirements document" — not what the document contained.
5. Logs are saved locally. You can review, edit, or delete them anytime.

### What It Doesn't Do

- It does not record your prompts or Claude's responses verbatim
- It does not capture proprietary business content, code, or data
- It does not report on individuals to management — analysis is always aggregated
- It does not affect your performance evaluation in any way
- It cannot see anything outside of your Claude Code session

### Why It Matters

You are among the first PMs at Capital One to use agentic AI tools for real work. Your experience — the wins, the struggles, the surprises — will directly shape how we roll this out to everyone. Every research log you generate makes the eventual training better, the starter kits more useful, and the support structures more effective.

---

## Tips from Early Adopters

**Start with output you can evaluate.** Draft something you'd normally write yourself, so you can judge quality.

**Be more specific than you think you need to be.** "Write a PRD" is a weak prompt. "Write a PRD for [type of feature] following [this template], targeting [this audience], emphasizing [these concerns]" gets dramatically better results.

**Iterate, don't restart.** If the output is 70% right, tell Claude what to fix rather than starting over. "The second section is too vague — add specific acceptance criteria" is better than "Try again."

**Work in files, not just chat.** Ask Claude to save output as files in your project. This builds a library of artifacts you can reference and reuse.

**Tell Claude what you didn't like.** "That was too generic" or "I need this to be more data-driven" helps Claude learn your preferences within the session.

**Don't copy-paste when you don't have to.** If you need to send something via Slack or email, you can always copy from the Markdown file. But try doing the authoring and revision in Claude Code rather than pasting into Google Docs to edit there.

---

## Getting Help

- **Trailblazers Slack channel**: [channel name] — ask questions, share discoveries, commiserate
- **Office hours**: [schedule] — drop in for live help with setup, skills, or workflow design
- **Your SWE teammate**: They're using Claude Code too. Compare notes. Find collaboration patterns.
- **Just ask Claude**: "How do I do X in Claude Code?" or "What's the best way to approach Y task?" — Claude can often teach you what you need in the moment.

---

## What Success Looks Like

By the end of the pilot, a successful PM participant will:

- Have a customized `CLAUDE.md` that reflects their role, preferences, and workflows
- Be comfortable authoring and reviewing work in Markdown
- Be able to delegate a variety of PM tasks to the agent with effective instructions
- Have identified at least 2-3 recurring workflows where agent assistance saves significant time
- Have an informed perspective on where agents add the most value for PM work — and where they don't
- Have contributed research data that helps their fellow PMs

You don't need to become a developer. You need to become someone who can work effectively alongside AI agents and the developers who build with them. That's the goal.
