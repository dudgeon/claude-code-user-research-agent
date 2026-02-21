# Trailblazers Research Approach: Executive Summary

## The Proposal

Embed lightweight, consent-based research instrumentation directly into the Trailblazers pilot participants' Claude Code configuration. The AI agent itself becomes the research instrument — observing usage patterns, classifying behaviors against a maturity model, and generating structured session logs that inform our organization-wide AI adoption strategy.

## Why This Matters

Capital One has hundreds of product managers. The Trailblazers pilot includes a handful. Every insight we extract from this pilot has a massive multiplier — it shapes the training, tools, and support structures for every PM who follows.

Traditional pilot research (surveys, interviews, observation) is expensive, delayed, and biased by recall. This approach captures data in real-time, in context, with zero additional burden on participants. It's also a perfect demonstration of the agent-native approach we're trying to teach: we're using the agent to study how people learn to use the agent.

## How It Works

Each pilot PM adds a brief paragraph to their `CLAUDE.md` (the agent's configuration file) and receives a pre-installed "research log" skill. During normal work, the agent passively observes behavioral patterns. At the end of each session, it offers to generate a 30-60 line structured log covering:

- What type of PM work was performed (categories, not content)
- How the PM interacted with the agent (delegation style, iteration patterns)
- Comfort level with the environment (terminal, Markdown, file system)
- Configuration activity (customization, skill use)
- Friction points and breakthroughs
- Maturity classification across six dimensions

## What It Does NOT Do

- Does NOT record prompts, responses, or proprietary content
- Does NOT create individual performance assessments
- Does NOT transmit data automatically — PMs review logs locally before any collection
- Does NOT affect the work experience — research is secondary to the actual task

## What We Get

| Week | Deliverable | Impact |
|---|---|---|
| 2 | Early friction identification | Unblock stuck participants; quick-win interventions |
| 4 | Adoption archetypes and patterns | Segment PMs for tailored support in future cohorts |
| 6 | Data-backed scaling recommendations | Training curriculum, starter kits, tool selection |
| 8 | Validated maturity model + pilot retrospective | Readiness assessment framework for all future PMs |

## What We Need

1. **Approval** to include the research component in the Trailblazers pilot
2. **Compliance review** of the CLAUDE.md addition and research log skill (provided)
3. **5 minutes** in the participant onboarding session to explain the research component
4. **A collection mechanism** for aggregating logs (shared repo recommended)

## The Meta-Argument

If we can't use an AI agent to efficiently study AI agent adoption — if we fall back to manual surveys and interviews — we've already demonstrated that we haven't internalized the agent-native approach we're trying to teach. This research method is the strategy in miniature.
