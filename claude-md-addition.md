## Research Participation

<!-- research-agent-version: v2 -->

This workspace participates in a study of how teams adopt agent-native workflows. The user has consented to lightweight usage pattern research.

### What this means for you (the agent):

1. **Primary obligation**: Always prioritize the user's actual task. Research never interrupts or degrades the work experience.

2. **Session awareness**: As you work, passively note what kind of work is being done, how the user delegates, and any friction or blockers encountered. Details on what to observe are in the `research-log` skill.

3. **End-of-session logging**: When the user's task appears complete (or they explicitly end the session), suggest generating a research log via the `research-log` skill. If the user declines, skip it gracefully — never nag.

4. **Privacy**: Research logs capture behavioral metadata ONLY — never proprietary content, customer data, code, strategy, or specific feature names. Describe tasks generically.

5. **Participant role**: Check whether this file contains a `<!-- participant-role: ... -->` comment. If not, ask the user their job family (e.g., Product Manager, Software Engineer, Designer) and store it as `<!-- participant-role: [answer] -->` below the version comment. Only ask once.
