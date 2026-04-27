# AI Agent Workspace

A starter template for building a focused AI agent tailored to one specific goal.
Clone this repository, follow the setup steps, and your agent is ready to use.

---

## Requirements

- [Claude Code](https://docs.claude.ai/en/docs/claude-code/overview) installed
- [Node.js](https://nodejs.org) v18 or later (for `npx` commands)

---

## Getting Started

### 1. Clone this repository

```bash
git clone https://github.com/your-org/ai-agent-workspace.git my-agent-name
cd my-agent-name
```

> Tip: name the folder after what the agent will do.
> Example: `seo-content-agent`, `competitor-monitor`, `pr-reviewer`

### 2. Install required skills

```bash
npx skills add https://github.com/vercel-labs/skills --skill find-skills
```

### 3. Configure environment variables

```bash
cp .env.example .env
```

Open `.env` and fill in the credentials relevant to your agent's goal:

```
# WordPress — needed if the agent publishes content
WP_SITE_URL=https://yoursite.com
WP_USERNAME=your_username
WP_APP_PASSWORD=your_application_password
```

> To generate a WordPress Application Password:
> Admin → Users → Profile → Application Passwords → Add New

### 4. Run the setup wizard

Open Claude Code in this directory, then ask:

```
Read and follow SETUP.md
```

Claude will analyze your website, ask about your agent's goal, and generate
the config files in `agent-config/`.

### 5. Start using the agent

Once setup is complete, give the agent its first task. The setup wizard
will suggest a starter prompt based on your stated goal.

---

## Project Structure

```
.
├── README.md                        # This file
├── CLAUDE.md                        # Agent instructions (read by Claude Code)
├── SETUP.md                         # Setup wizard
├── .env.example                     # Environment variable template
├── agent-config/                    # Generated during setup
│   ├── business-context.md          # Business profile and brand voice
│   ├── agent-goal.md                # Agent purpose, input, output, autonomy
│   ├── skills-config.md             # Available and requested skills
│   └── activity-log.md              # Auto-maintained log of agent actions
└── .claude/
    ├── settings.json                # Tool permissions
    └── skills/
        ├── find-skills/             # Discover new skills from the ecosystem
        ├── wordpress/               # Create and manage WordPress content
        └── ubersuggest/             # Keyword research and competitor analysis
```

---

## One Agent, One Goal

This template is designed for **focused agents** — each clone handles one
specific task. If you need multiple agents, clone this repo multiple times:

```
seo-content-agent/        ← finds keyword gaps and creates draft pages
competitor-monitor/       ← tracks competitor site changes weekly
pr-reviewer/              ← reviews pull requests before merge
```

This keeps each agent's context small, its skills relevant, and its
behavior predictable.

---

## Adding More Skills

If the agent needs a capability that isn't installed, ask:

```
Find and install a skill for [what you need]
```

The `find-skills` skill will search the ecosystem and recommend verified options.

To manually browse and install skills:

```bash
npx skills add vercel-labs/agent-skills --skill [skill-name]
```

Browse available skills at [skills.sh](https://skills.sh).

---

## Customization

| What to change              | Where                               |
|-----------------------------|-------------------------------------|
| Business info & brand voice | `agent-config/business-context.md`  |
| Agent purpose & autonomy    | `agent-config/agent-goal.md`        |
| Active skills list          | `agent-config/skills-config.md`     |
| Tool permissions            | `.claude/settings.json`             |
| Agent core behavior         | `CLAUDE.md`                         |
| Setup questions             | `SETUP.md`                          |