# Trailblazers CLAUDE.md Addition

## Overview

This is the text that each Trailblazers pilot participant adds to their project-level `CLAUDE.md` file. It should be appended to whatever project-specific instructions already exist.

The design principles:

- **Minimal**: ~15 lines. Does not interfere with the PM's actual work.
- **Transparent**: The PM can read exactly what it does. No hidden instrumentation.
- **Non-intrusive**: The agent continues to prioritize the PM's actual task. Research logging happens at natural breakpoints, not mid-task.
- **Informative**: Tells the agent enough about the research context to generate useful classifications without over-specifying.

## The Addition

```markdown
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

3. **End-of-session logging**: When the user's primary task appears complete (or they explicitly end the session), suggest generating a research log by invoking the `research-log` skill. If the user declines or seems busy, skip it gracefully — never nag.

4. **Privacy guardrails**: Research logs capture behavioral metadata ONLY. Never include: proprietary business content, customer data, code, strategy details, specific feature names, or anything that would identify the specific product or initiative being worked on. Describe tasks generically (e.g., "drafted a product requirements document" not "drafted the PRD for Project Falcon credit card rewards redesign").

5. **Maturity reference**: Classify observed behaviors using the Trailblazers PM Agent-Native Maturity Model (dimensions: Environment Fluency, Delegation Sophistication, Configuration Maturity, Task Breadth, Integration Depth, Meta-Cognitive Practice; each Level 1-5). Only classify dimensions where you have clear signal from this session.
```

## Installation Instructions for Participants

Share with each PM during onboarding:

---

**Adding the Trailblazers research snippet to your CLAUDE.md:**

1. Open your project in Claude Code
2. If you don't have a `CLAUDE.md` file yet, create one: the agent can help you with this
3. Append the Trailblazers Research Participation section (provided separately) to the end of your file
4. Copy the `research-log` skill file into your project's `.claude/skills/` directory (create the directory if it doesn't exist)
5. That's it. Claude will now be aware of the research context and will offer to generate a session log when your work is done.

**What you should know:**

- Research logs capture what *kind* of work you did and how you interacted with the agent, NOT the content of your work
- You can review any log before it's shared — they're just Markdown files in your `.claude/research-logs/` directory
- You can skip logging any session — just say "skip the log" if the agent offers
- You can edit or delete any log at any time
- Logs will be collected [weekly/biweekly] via [collection mechanism TBD — could be a simple script, shared repo, or manual upload]

---

## Customization Notes

The addition above is a starting template. Adjust for your specific context:

- **Collection mechanism**: The `[collection mechanism TBD]` needs to be filled in based on your infrastructure. Options: shared git repo that participants push to, a simple upload form, a collection script, or manual Slack/email submission.
- **Session end detection**: "When the user's primary task appears complete" is intentionally soft. In practice, the agent will use natural signals: the user saying "thanks," long pauses, explicit session-ending language. The research skill can also be invoked manually at any time.
- **Maturity model reference**: The full maturity model is referenced but not included in the CLAUDE.md (too long). It's embedded in the research skill. If you want the agent to have direct access, consider including it as a separate reference doc in the project.
