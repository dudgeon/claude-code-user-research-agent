## Trailblazers Research Participation

<!-- research-agent-version: v1 -->

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
