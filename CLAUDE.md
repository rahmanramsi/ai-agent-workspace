# AI Agent Workspace

This is a configurable AI agent workspace. The agent researches, analyzes data,
and executes actions based on findings — guided by the team's business context
and available skills.

> **First time setup?** Ask Claude to read and follow `SETUP.md`.

---

## Agent Configuration

@./agent-config/business-context.md
@./agent-config/agent-goal.md
@./agent-config/skills-config.md

---

## Core Behavior

### Before Taking Any Action
- Read agent-config files to understand business context, team goals, and autonomy level.
- Cross-reference findings with business context before making recommendations.
- Never assume — if context is unclear, ask for clarification.

### Decision Making
- When data clearly supports an action (e.g., high-volume keyword with no existing page),
  proceed according to the autonomy level defined in `agent-goal.md`.
- Draft-first is always the safer default when autonomy level is ambiguous.

### Skills Usage
- Only use skills listed as **available** in `skills-config.md`.
- If a task requires a capability not in the skills list, use the `find-skills` skill
  to search for an appropriate one before improvising.
- Never perform actions outside the declared skill set without explicit user approval.

### Output Quality
- Always prefer accurate over fast.
- Match tone and conventions defined in `business-context.md`.
- Follow the agent's purpose and constraints defined in `agent-goal.md`.

### Activity Logging
After every action that produces an external result (page created, file committed,
skill installed, etc.), append an entry to `agent-config/activity-log.md`.

**Entry format:**

    ## {YYYY-MM-DD HH:MM}
    - **Action**: {what was done}
    - **Skill**: {skill used}
    - **Trigger**: {what prompted this — user request, scheduled trigger, or data finding}
    - **Result**: {outcome, URL, file path, or other reference}
    - **Status**: {Completed / Draft pending review / Failed — {reason}}

**Rules:**
- Always append — never overwrite or delete existing entries.
- Log after execution, not before.
- If an action fails, log it with Status: Failed and a brief reason.
- Research-only sessions with no external output do not need a log entry.