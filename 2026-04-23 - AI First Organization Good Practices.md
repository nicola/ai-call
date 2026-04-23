# AI Call — AI First Organization Good Practices
**Date:** 2026-04-23

---

## Q1: What's the first good practice that comes to mind?

**Answer:** First, there should be an additional folder concept: an **apps folder** where everyone can develop apps — visualizations, computations, or scripts — on top of the context data.

The first rule is **context first**. If there's new information, a meeting, internal knowledge — it should be dropped into the context.

Then there are **levels of AI usage**:
1. **Single-threaded**: Use AI through a chatbot, one conversation at a time.
2. **Multi-agent**: Ask the AI to spin up multiple agents to fulfill a task. You can even have multiple agents do similar work, then pick the output you like most.
3. **Autonomous**: Don't even prompt the AI — just give it all the context and the latest to-dos, and it figures out what the right thing to do is. Ideally it creates PRs into the context.

There are also new experiments like **auto-research**, where you ask the AI to run in a loop to improve some metric.

Another key practice: **separate data from apps**. Don't hardcode data into applications. Keep data independent so it can be used by as many apps as possible.

---

## Q2: Are there practices around how humans review what the AI produces?

**Answer:** A core practice is to **turn the problem into a verification problem**. Instead of designing one version of something yourself, ask the AI to generate multiple versions for you to review — all in the form of pull requests. You pick which ones you like and which ones you don't.

Some things require human verification, but there are also things where you can scale by building AI to verify. This is an open problem.

---

## Q3: How does team collaboration change in this model?

**Answer:** People should ask the AI to interact with the folder — ideally a person should not directly edit files. You tell the AI to draft what you want, and it figures it out. Collaboration happens in the form of **concurrent pull requests**.

This approach currently requires software like Git, which isn't for everyone. In the future, better software will emerge for this workflow.

---

## Q4: How should someone get started?

**Answer:** Start with an empty coding agent — Claude, Codex, or Pi (personal favorite). Open it in an empty folder. Ideally use the `agents.md` from this project, or just describe what you want to do and ask the AI to help you scale it.

The first skill to install is **AI Call**, so you can drop your context in the form of a conversation. Make sure you have a transcription tool like [Handy](https://handy.computer).

---

## Summary

Good practices for an AI-first organization center on six principles: context first (always feed new information into the shared context), multiple levels of AI engagement (from single-threaded chat to fully autonomous agents), turning creation into verification (let AI generate options, humans pick), separating data from apps for reusability, collaborating through concurrent PRs rather than direct file editing, and getting started simply with a coding agent, an empty folder, and the AI call skill.
