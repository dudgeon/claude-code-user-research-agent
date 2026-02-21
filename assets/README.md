#Prompt
```
I want you to help me think through a project.

Context: my new job is to lead the diffusion of ai tools and methods among product managers at my company.

Many product managers are not familiar with GitHub, Markdown, IDEs, the CLI — much less Claude code and agentic coding assistants. They live in Google Docs and Jira and slack—and need to venture beyond.

I believe that mature adoption of Claude code, expertise in its control primitives, and interfacing with software development teams that are increasingly adopting these tools, will be critical to our success. It will be insufficient to copy and paste text from our legacy tools into Gemini/chatgpt—these PMs need to become more agent native.

We are kicking off a new trial called “Trailblazers”. A small number of hand-picked teams, including SWE and PM (and in some cases design). Will gain access to and be expected to use Claude Code for a defined period of time.

To me this is an ideal venue within which to perform user research. I want to understand how the PMs are using Claude code; what kind off of tasks they are performing, how often they are using the tools, what issues they are hitting. How it plugs into dev workflows; are they doing copy/paste with legacy tools or becoming more agent native? Are they modifying their Claude.md, building and refining skills, building commands, etc. are there skill packs they are importing and if so which ones? Are those skills being invoked or sitting unused? Etc. etc etc.

To me, this is a perfect task for… an agent.

I want you to consider my higher level learning goals (growth and division of agent-native accelerated product management among ALL product managers, not just pilot participants), the strategies they will inform (eg training, tool selection, starter Claude.md/skill.md), and the kind of insights that I will need to build and execute this strategy.

Then consider how to gather this information: I think that if all pilot participants installed/added a couple lines of instruction to their Claude.md, and added a user research skill.md, we could gather a TON of user research that would inform our effort and benefit all product managers.

Please take your time and think this through thoroughly. Generate as many documents as you think will help helpful both for this exercise and future work in the initiative.
```

# Response
This is a genuinely exciting project, Geoff — using the agent as its own ethnographic research instrument is a sharp insight. Let me think through the full system and build out the documents.

Let me start by reading relevant skills for document creation, then I'll build this out comprehensively.Now let me build out the full document suite. I'm going to create several interconnected pieces:Now let me save this to your brain for future reference and then present all the files.Here's the complete nine-document toolkit. Let me walk you through the architecture of what I built and the key design decisions:

**The core insight I ran with**: the agent-as-ethnographer approach is powerful precisely because it eliminates the observer's paradox that plagues traditional user research. PMs just work. The agent watches and classifies. The data is richer than surveys, more consistent than interviews, and costs nothing in participant time.

**The maturity model** (doc 02) is the spine of everything. Six dimensions, five levels each. I encoded it as a compact shorthand (`E3-D2-C1-T2-I1-M2`) that the research skill uses in every log. This makes longitudinal tracking and cross-participant comparison tractable — you can literally sort a spreadsheet by maturity strings to find clusters.

**The CLAUDE.md addition** (doc 03) is deliberately ~15 lines. I resisted the urge to make it comprehensive because the *evolution* of the CLAUDE.md is itself one of the richest maturity signals. Starting heavy would mask that.

**The research skill** (doc 04) is the operational heart. It generates structured logs with consistent sections — task categories, delegation style indicators, environment interaction markers, friction/wins, and the maturity classification. All behavioral metadata, never proprietary content. The privacy guardrails are baked into the skill instructions, not left to participant judgment.

**The starter skill pack** (doc 08) includes 4 concrete skills beyond the research skill. I was deliberate about what to include (universal PM tasks) and what to exclude (team-specific, compliance-sensitive, or tools that Claude Code isn't ideal for). The utilization data from these known skills is itself a research signal.

**The meta-argument** in the executive pitch (doc 09) is the one I'd lead with: if we can't use an agent to study agent adoption, we've already failed to internalize the approach we're trying to teach.

A few things I'd want to discuss with you as next steps: the log collection mechanism (shared git repo is ideal but may be a maturity hurdle for Day 1 PMs), whether compliance needs to review the skill before deployment, and whether you want to instrument the SWE participants too or keep the research PM-focused. Also saved a summary to your brain for future reference.
