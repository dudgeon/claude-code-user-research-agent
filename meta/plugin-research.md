# Could a Claude Code Plugin Simplify Research Agent Distribution?

Research date: 2026-02-22

## Current Install Process

Today, participants install the research agent by:

1. **Adding a snippet to their CLAUDE.md** — copy-paste from `claude-md-addition.md`
2. **Creating `.claude/skills/research-log.md`** — copy-paste from `research-log-skill.md`

This is intentionally minimal (two files, ~2 minutes), but it still involves manual file creation, navigating hidden directories, and getting the content right. For non-technical users (PMs, designers), even "create a file at `.claude/skills/research-log.md`" can be a stumbling block.

## What Claude Code Plugins Are

Claude Code plugins are bundled extension packages that can include:

- **Skills** (custom slash commands and auto-triggered behaviors)
- **Agents** (specialized subagents)
- **Hooks** (event handlers: SessionStart, SessionEnd, PreToolUse, etc.)
- **MCP servers** (external tool connections)
- **Settings** (configuration applied when the plugin is enabled)

Plugins are distributed through **marketplaces** — git repositories containing a `.claude-plugin/marketplace.json` catalog. Users install with a single command:

```
/plugin marketplace add dudgeon/claude-code-user-research-agent
/plugin install research-agent@dudgeon-claude-code-user-research-agent
```

Or even simpler if the plugin repo is also the marketplace:

```
/plugin install research-agent
```

Plugins namespace their skills (e.g., `/research-agent:research-log`), support versioning, and can auto-update when the source repo is updated.

**Key references:**
- [Create plugins](https://docs.anthropic.com/en/docs/claude-code/plugins)
- [Discover and install plugins](https://docs.anthropic.com/en/docs/claude-code/discover-plugins)
- [Plugins reference](https://docs.anthropic.com/en/docs/claude-code/plugins-reference)
- [Skills docs](https://docs.anthropic.com/en/docs/claude-code/slash-commands)

## What a Plugin Version Would Look Like

### Proposed structure

```
claude-code-user-research-agent/
├── .claude-plugin/
│   ├── plugin.json            # Plugin metadata
│   └── marketplace.json       # Makes this repo its own marketplace
├── skills/
│   └── research-log/
│       └── SKILL.md           # The research-log skill (currently research-log-skill.md)
├── hooks/
│   └── hooks.json             # SessionEnd hook to prompt for logging
├── agents/
│   └── research-observer.md   # (optional) Agent with ambient observation instructions
├── README.md
├── assets/
│   └── ...
└── meta/
    └── ...
```

### plugin.json

```json
{
  "name": "research-agent",
  "description": "Lightweight research logging for agent adoption studies. Observes behavioral patterns during sessions and offers to generate a research log at session end.",
  "version": "2.0.0",
  "author": {
    "name": "Anthropic Research"
  }
}
```

### What each component replaces

| Current approach | Plugin equivalent |
|---|---|
| Copy snippet into CLAUDE.md | Plugin skill description + hooks provide context automatically |
| Create `.claude/skills/research-log.md` by hand | Plugin `skills/research-log/SKILL.md` installed automatically |
| User must remember to start new session | Plugin active immediately after install |

## The Key Design Question: Ambient Awareness

The current CLAUDE.md snippet does something subtle — it tells Claude to **passively observe behavioral patterns throughout the entire session**, not just at the end. This "always-on" context is what makes the research data rich. The snippet says:

> "As you work, passively note what kind of work is being done, how the user delegates, and any friction or blockers encountered."

This ambient awareness is straightforward with CLAUDE.md because Claude reads it at session start and it persists as context. Can a plugin replicate this?

### Options for ambient context via plugin

1. **Skill description with broad trigger**: The skill's `SKILL.md` can include a description that says "this skill should be loaded at session start" and contains the observation instructions. Claude Code loads skill descriptions to decide when to invoke them, so Claude would see the instructions. However, this only works if skill descriptions are loaded eagerly (at session start) rather than lazily. Need to verify this behavior.

2. **SessionStart hook**: A hook that runs at session start could print instructions to stdout. However, hooks execute shell commands — their output isn't injected into Claude's conversational context in the same way CLAUDE.md is. Hooks influence behavior through side effects, not through prompt injection.

3. **Plugin-level settings**: Plugins can apply settings when enabled. If there's a way to inject instructions into Claude's context via settings, this would work. But settings are typically configuration flags, not freeform instructions.

4. **Hybrid approach — plugin + thin CLAUDE.md line**: The plugin handles the skill installation and complexity, but the user still adds one line to CLAUDE.md:
   ```
   This workspace uses the research-agent plugin. Follow its observation guidelines.
   ```
   This is much simpler than the current multi-paragraph snippet.

5. **Agent component**: Plugins can include agents. A research-observer agent could carry the ambient instructions. However, agents are typically invoked for specific tasks, not loaded as persistent context.

**Assessment**: Option 4 (hybrid) is the most reliable. The plugin handles 90% of the install complexity; a one-line CLAUDE.md addition handles the ambient context. Option 1 is worth testing — if skill descriptions are loaded eagerly, the plugin alone may be sufficient.

## Pros of Moving to a Plugin

### For participants (install experience)
- **One command** vs. navigating hidden directories and copy-pasting file contents
- **No risk of copy-paste errors** — partial pastes, wrong file paths, encoding issues
- **Auto-updates** — push a new version, participants get it on next session without re-installing
- **Easy removal** — `/plugin uninstall` vs. hunting down files
- **Professional UX** — feels like installing a feature, not hacking config files

### For the research team (distribution & maintenance)
- **Versioning** — pin participants to specific versions, roll out updates incrementally
- **Marketplace catalog** — this repo can be its own marketplace, or plugins can be listed in a team marketplace
- **Hooks unlock new capabilities** — a SessionEnd hook could reliably prompt for logging without relying on Claude interpreting CLAUDE.md correctly
- **Analytics potential** — plugin install/uninstall events could track adoption
- **Team-wide deployment** — add the marketplace to `.claude/settings.json` in the team's shared repo and everyone gets it

### For the study itself (data quality)
- **Consistent install** — everyone runs the exact same version of the skill
- **Fewer "it's not working" issues** — the #1 failure mode today (file in wrong place, partial paste) goes away
- **SessionEnd hook** is more reliable than relying on Claude to remember CLAUDE.md instructions about end-of-session behavior

## Cons and Risks

### Plugin system maturity
- The plugin ecosystem is relatively new. While it's well-documented and Anthropic bundles 13 official plugins, the ergonomics for non-technical users installing third-party plugins are less battle-tested than copy-pasting files.

### Ambient context gap
- As discussed above, plugins don't have a clean equivalent of CLAUDE.md's always-on instructions. The research agent's value depends on ambient observation, not just end-of-session logging. A pure plugin approach may lose the "passively note patterns" behavior unless skill descriptions are loaded eagerly.

### Target audience familiarity
- The current audience is explicitly non-technical (PMs, designers). They may be unfamiliar with `/plugin` commands. That said, `/plugin install research-agent` is arguably simpler than "create a hidden directory, then create a file inside it, then paste this 270-line document."

### Participant role tracking
- The current CLAUDE.md snippet stores `<!-- participant-role: ... -->` as a comment in CLAUDE.md. A plugin would need an alternative storage mechanism — perhaps a `.claude/research-config.json` or a local settings value.

### Marketplace setup overhead
- Creating a marketplace requires adding `.claude-plugin/marketplace.json` to this repo. This is a one-time setup cost and is straightforward.

## Sideloading: Plugin Benefits Without a Marketplace

Follow-up research (2026-02-22) into whether the plugin structure can be used
without the overhead of setting up and teaching participants about marketplaces.

### Three sideload approaches

**1. `claude plugin add ./local-path` (one-time install from clone)**

```bash
git clone https://github.com/dudgeon/claude-code-user-research-agent ~/research-agent
claude plugin add ~/research-agent
```

This installs the plugin persistently (written to `~/.claude/plugins/installed_plugins.json`) without any marketplace. The user clones the repo once, runs one command, done. Updates require a `git pull` in the cloned repo and reinstall.

- Pros: No marketplace concept to explain. Two commands total. Persists across sessions.
- Cons: Requires git clone first. Updates are manual. There is a [known bug](https://github.com/anthropics/claude-code/issues/12457) where local directory installs sometimes fail to persist — worth testing before committing to this path.

**2. `--plugin-dir` flag (zero-install, dev-style)**

```bash
claude --plugin-dir ~/research-agent
```

Loads the plugin for a single session without any installation step. No marketplace, no `plugin add`, no persistence.

- Pros: Simplest possible command. No install state to manage.
- Cons: Must be passed every time Claude Code starts. Not practical for daily use unless wrapped in a shell alias. Non-technical users won't want to manage CLI flags.

**3. Project-level `settings.json` (team-wide, zero participant action)**

If the research team controls a shared repo, they can add to `.claude/settings.json`:

```json
{
  "enabledPlugins": {
    "research-agent@local": true
  }
}
```

Combined with including the plugin directory in the repo itself (e.g., at `.claude/plugins/research-agent/`), this means every team member who clones the repo gets the plugin automatically with zero manual steps.

- Pros: True zero-touch install for participants. Team-wide consistency. No marketplace.
- Cons: Requires the research team to commit plugin files into each participating project repo. Only works for repos the research team controls or can get PRs merged into.

### Caveats discovered

- **Plugin cache behavior**: When installed, Claude Code copies the plugin to `~/.claude/plugins/cache/` rather than running from the source directory. This means changes to the source require reinstallation. Symlinks within the plugin directory are followed during copy.
- **`settings.local.json` bug**: If `enabledPlugins` only exists in `settings.local.json` (not in `settings.json`), plugins are silently ignored. Workaround: add an empty or false-valued `enabledPlugins` in `settings.json` so the merge works.
- **No direct git-URL install**: Unlike `npm install github:user/repo`, there doesn't appear to be a way to `claude plugin add https://github.com/...` directly. The user needs either a local clone or a marketplace. This is the main gap.

### Assessment: Which sideload path fits this project?

For this research agent, the **hybrid of approaches 1 and 3** is most promising:

| Audience | Approach |
|---|---|
| Individual participants (PMs, designers) | Clone + `claude plugin add ./path` — two commands, explained in README |
| Team-wide rollout | Commit plugin into shared repo + `settings.json` — zero participant action |
| Research team testing | `--plugin-dir` — instant iteration during development |

The key insight: **the plugin structure is valuable even without a marketplace**. It gives you namespacing, hooks, proper skill packaging, and a clean uninstall path. The marketplace is a distribution channel, not a prerequisite for the plugin format itself.

If/when the marketplace infrastructure becomes worth the overhead (many teams, public distribution), the same plugin structure works — you just add a `marketplace.json` to this repo. The sideload path is forward-compatible.

## Recommendation

**Yes, a plugin would meaningfully simplify the install — and a marketplace is not required to get the benefits.**

### Suggested approach

1. **Restructure this repo as a plugin** — add `.claude-plugin/plugin.json`, move the skill into `skills/research-log/SKILL.md`. Skip `marketplace.json` for now.
2. **Add a SessionEnd hook** — reliably prompt for research logging instead of relying solely on CLAUDE.md interpretation
3. **Test whether skill descriptions provide ambient context** — if the skill's description is loaded at session start, the plugin alone may be sufficient. If not, fall back to the hybrid approach (plugin + one-line CLAUDE.md addition)
4. **Test `claude plugin add ./path` reliability** — verify the known persistence bug is resolved, or document the workaround
5. **Keep the current manual install as a fallback** — document both paths in the README

### Migration path

The restructuring is non-breaking. The existing files (`claude-md-addition.md`, `research-log-skill.md`) can remain alongside the plugin structure for users who prefer manual install. The README would offer three paths:

> **Option A (recommended):** Clone this repo, then run `claude plugin add ~/path-to-clone`
>
> **Option B (team rollout):** Commit the plugin into your project repo and add to `.claude/settings.json`
>
> **Option C (manual):** Follow the copy-paste instructions below

A marketplace can be added later if broader public distribution is needed — the plugin structure is the same either way.

### Open questions to investigate

- Do plugin skill descriptions get loaded eagerly at session start, or only when a matching trigger is detected?
- Can a plugin's settings inject freeform instructions into Claude's context?
- What's the UX for `/plugin marketplace add` for a user who has never used plugins before? Is there a confirmation flow?
- Can the participant-role tracking (currently a CLAUDE.md comment) be stored in plugin-local config?
