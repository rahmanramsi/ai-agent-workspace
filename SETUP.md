# Workspace Setup Wizard

Read this file completely before starting. Then follow the steps below
to configure this workspace.

---

## Overview

Your goal is to configure this workspace for one specific agent with one
specific purpose. Each agent should do one thing well — not everything.

**Files to generate:**
- `agent-config/business-context.md`
- `agent-config/agent-goal.md`
- `agent-config/skills-config.md`

**Rules:**
- Never ask for something you can reasonably detect from the website.
- When presenting findings, be explicit about your confidence level.
- Only ask follow-up questions for data that is missing or uncertain.
- Derive follow-up questions from the agent's stated goal — not from a preset list.

---

## Step 1 — Request Website URL

Start with this message:
> "Hi! I'll help you set up this AI Agent Workspace. To get started,
> what is your website URL?"

Wait for the URL, then proceed to Step 2.

---

## Step 2 — Analyze the Website

Fetch and analyze the website. Extract the following:

| Data | Where to look |
|------|--------------|
| Business name | Page title, logo alt text, `<meta>` tags, footer |
| Industry / sector | Homepage copy, about page, product/service descriptions |
| Target audience | Hero section copy, product descriptions, CTAs |
| Website platform | HTML source (`<meta name="generator">`, script/link tags, URL patterns) |
| Tone of voice | Analyze 3–5 paragraphs of copy — formal/casual, technical/plain, etc. |

If the homepage is not enough, also check:
- `/about` or `/about-us`
- `/services` or `/products`

**If the website is inaccessible** (login-required, JS-heavy, or returns an error):
> "I wasn't able to fully analyze your website. Could you briefly describe:
> your business name, industry, target audience, and tone of voice?"

---

## Step 3 — Present Findings & Confirm

Present findings in this format:

> "Here's what I found from your website. I'll flag anything I'm not fully sure about."
>
> - **Business name**: {value} ✓
> - **Industry**: {value} ✓
> - **Target audience**: {value} ✓
> - **Website platform**: {value} ✓
> - **Tone of voice**: {description} — *I'm less certain about this one.
>   Does this feel right, or would you describe it differently?*

**Confidence rules:**
- Mark with ✓ if you are confident (clear, unambiguous evidence from the site).
- Flag with a follow-up question if you are uncertain or the data is ambiguous.
- If a data point is completely missing, ask directly:
  > "I couldn't determine {data point} from your website. Could you describe it briefly?"

Wait for the user to confirm or correct before continuing.

---

## Step 4 — Define the Agent's Goal

Ask:
> "What is the main goal of this agent? Describe what you want it to do
> in one or two sentences."
>
> *Examples to help you think about it:*
> - *"Find keyword gaps compared to competitors and create draft pages for each opportunity"*
> - *"Monitor competitor websites weekly and summarize what has changed"*
> - *"Research a given topic and write a full SEO-optimized blog post"*
> - *"Review pull requests and flag potential bugs or style violations"*
> - *"Find and fix accessibility issues across the codebase"*
>
> *Your agent doesn't have to match these examples — describe what you actually need.*

Wait for the answer, then proceed to Step 5.

---

## Step 5 — Ask Goal-Specific Follow-Up Questions

Based on the stated goal, identify what the agent needs to know to operate
effectively. Think in three categories:

**1. Input** — Where does the agent get its data?
Ask if not clear from the goal. Examples:
- Does it monitor specific competitor URLs, or discover them automatically?
- Does it analyze a specific branch, or the whole repo?
- Is the topic given by the user each time, or does the agent decide?

**2. Output** — What does the agent produce and where does it go?
Ask if not clear from the goal. Examples:
- Should the result be published, saved as draft, sent as a report, or committed?
- Is there a specific format, template, or structure to follow?

**3. Autonomy** — How much can the agent do without human approval?
Always ask this, regardless of the goal:
> "When the agent is ready to take action (e.g., publish, commit, send) —
> should it proceed automatically, or pause and wait for your approval first?"

Only ask questions that are genuinely needed for the stated goal.
Do not ask generic questions that don't apply.

---

## Step 6 — Skills Inventory

Based on the stated goal, suggest the skills that are likely needed:

> "For this goal, I think the agent will need: {list of suggested skills}.
> Are there any other tools or integrations you want to add or remove?"

After confirming:
- Check which suggested skills already have a folder in `.claude/skills/`
- Note which ones are missing — they will be listed in `skills-config.md`

---

## Step 7 — Generate Config Files

Create the `agent-config/` directory if it doesn't exist, then generate:

### `agent-config/business-context.md`

    # Business Context

    ## Business Profile
    - **Name**: {business_name}
    - **Industry**: {industry}
    - **Target Audience**: {target_audience}
    - **Website URL**: {url}
    - **Website Platform**: {platform}

    ## Brand Voice
    {tone of voice description}

---

### `agent-config/agent-goal.md`

    # Agent Goal

    ## Purpose
    {one or two sentence description of what this agent does}

    ## Input
    {where the agent gets its data}

    ## Output
    {what the agent produces and where it goes}

    ## Autonomy Level
    {auto / approval required}

    ## Additional Context
    {any other relevant details gathered from follow-up questions}

---

### `agent-config/skills-config.md`

    # Skills Configuration

    ## Available Skills
    {list each skill that has a matching folder in .claude/skills/, with a one-line description}

    ## Requested Skills (Not Yet Installed)
    {list skills needed for the goal that don't have a SKILL.md yet}

    ## Notes
    - To install a missing skill, ask: "find and install a skill for [name]"
    - All skills are located in `.claude/skills/`

---

## Step 8 — Confirm & Complete

After generating the files, show this summary:

> "Setup complete! This agent is configured to: **{agent goal in one sentence}**
>
> **Installed skills**: {list}
> **Skills to install**: {list or "none"}
>
> You're ready to go. Here's a prompt to try first:
> _{suggest a concrete starter prompt directly relevant to the stated goal}_"