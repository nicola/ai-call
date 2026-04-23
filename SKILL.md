---
name: ai-call
description: Create or start an AI call. Use "create an AI call about..." to generate a call.md file to send to someone. Use "start an AI call about..." or "start an AI call from call.md" to run an interactive call. Triggers on "create an AI call", "start an AI call", "interview me about", "ask me questions about", "run an AI call about".
---

# AI Call

An AI call is a structured conversation where an AI asks questions one at a time, follows up based on answers, and produces a clean markdown transcript. There are two modes:

1. **Create a call** — Generate a `call.md` file that can be sent to someone else to run later.
2. **Start a call** — Run an interactive call right now, either from a prompt or from a `call.md` file.

---

## Mode 1: Create a Call

When the user says "create an AI call about..." or "generate an AI call for...":

1. Read the user's prompt — topic, questions, context, who it's for.
2. Generate a `call.md` file with the following format:

```markdown
# AI Call: [Title]

## Context
[Brief description of why this call is being conducted and any background the interviewee should know.]

## Questions
1. [Question 1]
2. [Question 2]
3. [Question 3]
...

## Notes
- [Any instructions for the AI conducting the call, e.g. "deep dive on question 2", "keep it under 10 minutes", "follow up on technical details"]

---
*To run this AI call, install the [AI Call skill](https://github.com/nicola/ai-call) if you haven't already.*
```

### Guidelines for creating calls

- **Refine the user's input.** If they give rough bullet points, turn them into clear, well-phrased questions.
- **Add context.** Help the future interviewee understand what the call is about.
- **Keep it focused.** 3-7 questions is usually right. Don't overload.
- **Include notes** if the user specifies any preferences about depth, tone, or follow-up behavior.
- **Save as `call.md`** in the current directory (or a custom filename if the user specifies one).

The user can then send this file to someone via email, messaging, or calendar invite. The recipient runs it with their preferred AI tool.

---

## Mode 2: Start a Call

When the user says "start an AI call about...", "interview me about...", "ask me questions about...", or "run an AI call about/from...":

### Determining the call source

- **From a prompt:** The user provides a topic, questions, or description inline. You plan the call from that.
- **From a `call.md` file:** The user says "start an AI call from call.md" or similar. Read the file and use its questions, context, and notes to conduct the call.

### How It Works

1. Analyze the prompt or `call.md` file: derive questions, identify areas for deep-dives, determine when the call is complete.
2. Ask questions **one at a time**, wait for the user's response, then decide:
   - **Follow up** if the answer is incomplete, vague, or opens an interesting thread worth exploring
   - **Move on** to the next question if the answer is sufficient
3. When all questions are covered, wrap up and generate the transcript.

### Your Behavior During the Call

- **Be conversational, warm, and concise.** You're having a conversation, not administering a test.
- **Ask one question at a time.** Never list multiple questions. Wait for a response before continuing.
- **Listen carefully.** Reference what the user said. Don't repeat questions they already answered.
- **Follow up naturally.** If they mention something interesting, explore it briefly — but don't go off track.
- **Keep it focused.** The prompt or call.md defines the scope. Don't wander into unrelated territory.
- **Know when to stop.** When the goals are met, wrap up gracefully. Don't drag it out.
- **Be brief in your transitions.** A short acknowledgment ("Got it, thanks.") before the next question is fine. Don't over-explain or summarize after every answer.

### Starting the Call

1. Read the prompt or `call.md` carefully.
2. Internally plan: What are the key questions? What order makes sense? What follow-ups might be needed? (Do NOT share this plan with the user.)
3. Briefly greet the user and explain what the call is about (1-2 sentences max).
4. Ask the first question.

Example start:
> Hi! I'm going to ask you a few questions about [topic]. Let's get started.
>
> [First question]

### During the Call

After each user response:

1. Decide: follow up or move on?
2. If following up, ask a focused follow-up question.
3. If moving on, briefly acknowledge and ask the next question.
4. If all questions are done, move to wrap-up.

**Limit follow-ups:** Don't ask more than 2 follow-ups on a single question unless the prompt or call.md specifically asks for deep dives.

### Wrapping Up

When the call is complete:

1. Thank the user briefly.
2. Generate the transcript as a markdown file.

### Transcript Format

Save the transcript to a file called `YYYY-MM-DD - [Topic/Title].md` (using the current date and a short descriptive title). For example: `2026-04-23 - Distributed Systems Experience.md`

The transcript format:

```markdown
# AI Call — [Topic/Title]
**Date:** [YYYY-MM-DD]

---

## Q1: [Question as asked]

**Answer:** [User's response, cleaned up for readability but not edited for content. Keep their words, just fix obvious speech-to-text artifacts if any.]

### Follow-up: [Follow-up question if any]

**Answer:** [Response]

---

## Q2: [Next question]

**Answer:** [Response]

---

[...repeat for all questions...]

---

## Summary

[2-3 sentence summary of the key takeaways from the call]
```

### Transcript Rules

- **Preserve the user's words.** Clean up minor speech artifacts (ums, repeated words) but don't rewrite their answers.
- **Keep it readable.** Use proper formatting, paragraphs, punctuation.
- **Include follow-ups** nested under their parent question.
- **Add a brief summary** at the end highlighting the key points.

---

## Prompt Interpretation

The user's prompt can be:

- **A topic:** "my experience with Rust" → You generate appropriate questions
- **A list of questions:** "Ask: 1) ... 2) ... 3) ..." → You ask these in order
- **A job description or brief:** "Interview for senior engineer role at..." → You derive relevant questions
- **A mix:** "Ask about X, Y, Z. Deep dive on X." → You structure accordingly
- **A file reference:** "from call.md" → Read the file and follow its structure

If the prompt is vague, generate 3-5 thoughtful questions. If it's detailed, follow it closely.

## Examples

**Create a call:**
> "Create an AI call for my team about their experience with the new deployment pipeline. Ask about pain points, what's working, and suggestions."

**Start a call from a prompt:**
> "Start an AI call about my experience building distributed systems, specifically around consistency models and failure handling."

**Start a call from a file:**
> "Start an AI call from call.md"
