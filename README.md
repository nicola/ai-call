# AI Call

A skill that turns any AI coding agent into a structured interviewer. The agent asks questions one at a time, follows up based on your answers, and produces a clean markdown transcript.

Works with any agent that supports the [Agent Skills standard](https://agentskills.io): **pi**, **Claude Code**, **OpenAI Codex**, and others.

## What It Does

1. You provide a **prompt** — a topic, questions, or a job description
2. The AI asks questions **one at a time**, waiting for your response
3. It follows up if your answer is incomplete or opens an interesting thread
4. When done, it generates a clean markdown transcript with all Q&A pairs

**No API keys needed** — uses whatever model your agent is already running.

## Install

### Pi

```bash
# From npm
pi install npm:ai-call

# From git
pi install https://github.com/nicola/ai-call

# Pin a version
pi install npm:ai-call@1.0.0
pi install https://github.com/nicola/ai-call@v1.0.0
```

### Claude Code

```bash
# Global (available in all projects)
git clone https://github.com/nicola/ai-call ~/.claude/skills/ai-call

# Or project-level
git clone https://github.com/nicola/ai-call .claude/skills/ai-call
```

### OpenAI Codex

```bash
# Global
git clone https://github.com/nicola/ai-call ~/.agents/skills/ai-call

# Or project-level
git clone https://github.com/nicola/ai-call .agents/skills/ai-call
```

### Manual

Copy `SKILL.md` into your agent's skills directory. That's the only file that matters.

## Usage

Once installed, just ask your agent:

- *"Start an AI call about my experience with distributed systems"*
- *"Interview me about my leadership style"*
- *"Ask me questions about this job description: [paste JD]"*
- *"Run an AI call — ask about my top 3 projects and what I learned"*

The agent will ask questions one at a time, follow up naturally, and save a transcript as `YYYY-MM-DD - [Topic].md`.

## Examples

**Topic-based:**
> "Start an AI call about my experience building mobile apps"

**Question list:**
> "Ask: 1) What's your biggest technical challenge? 2) How do you handle disagreements? 3) What are you learning right now?"

**Job description:**
> "Interview me for this role: [paste job description]"

**Deep dive:**
> "Ask about my distributed systems experience. Deep dive on consistency models and failure handling. Cover 3-4 real projects."

## How It Works

This is a pure-prompt skill — no scripts, no dependencies, no API keys. The `SKILL.md` file contains instructions that tell the agent how to behave as an interviewer. Your agent loads these instructions when it detects a matching request.

The transcript is saved locally as a markdown file. Your data never leaves your machine (beyond whatever your agent's model provider already sees).
