# AI Call — AI First Organization README
**Date:** 2026-04-23

---

## Q1: What does "AI-first organization" mean to you? What's the core idea people should walk away with?

**Answer:** The operating system of organizations is changing. Previously people met in person, then moved to digital tools — files, databases, Notion, Slack. With AI, this changes again because AI has the power to organize all the content in an organization. Plus AI can be used as a form of worker — it can do work for us. An AI-first organization should have a new set of processes. The core goal of the README is to collect all the new concepts that are essential in an AI-first organization.

---

## Q2: What are the new concepts you'd want to cover?

**Answer:** Five core concepts:

**1. Context folder** — Every organization has implicit context, sometimes in documents, sometimes in people's heads. With AI and a shared context folder, you can just ask the AI to find answers. Context is built two ways: importing existing knowledge (converting docs to Markdown), and continuous updates via meetings and notes. The AI determines which context files need updating after a meeting — it maintains a living log of what has happened in the organization.

**2. AI Calls** — A call between a person and an AI. Can be scheduled by someone else, scheduled by an AI, or run on-demand. Use cases include organizing thoughts, being prompted with questions, brainstorming. A dedicated AI call skill has been created separately.

**3. Social Network folder** — A living directory of people, organizations, entities, and brands to track. Agents periodically scan profiles online, cross-reference with the organization's context, and check relevance. Over time it becomes a personalized social media feed — you can ask "what happened last week?" and get an AI-generated summary.

**4. Agents folder** — A dedicated folder where the organization crafts and maintains shared agents, so individuals don't have to recreate them. Example: an evaluator agent for reviewing proposals.

**5. Technical requirements** — Everything should be Obsidian-friendly (linking, tables, no duplication) and versioned with Git (change tracking, full log).

### Follow-up: How does the context folder update work in practice?

**Answer:** It's as simple as using an AI in a terminal or application. You continuously send content to it, it updates the context and creates a PR, and others review it. There's a human review step via PRs to keep quality in check.

### Follow-up: Can you clarify the intelligence folder vs agents?

**Answer:** These should be separated into two concepts: the **agents folder** (shared agent definitions the org maintains, which run ongoing) and the **social network folder** (the output — a living directory that agents keep updated, either when prompted or autonomously via tools like OpenClaw).

---

## Q3: Who is the audience for this README?

**Answer:** Not technical people — anyone. The document is meant to help and teach anyone what the new shape of an AI-first organization looks like.

---

## Q4: What's the relationship between the README and the agents.md?

**Answer:** The README teaches humans the concepts. The `agents.md` is the machine-readable version — it has the same notions well-spec'd for an AI to understand and perform the work. If someone installs the `agents.md`, then whenever they ask the AI to do something, it will follow the good practices dictated in it. Beyond concepts, there's also a "good practices" section to be developed later.

---

## Summary

Nicola envisions an AI-first organization as having a new "operating system" built around five core concepts: a context folder (living organizational knowledge maintained by AI via PRs), AI calls (structured conversations between humans and AI), a social network folder (proactively maintained directory of people and entities), an agents folder (shared agent definitions), and Git-versioned, Obsidian-friendly technical foundations. The README teaches these concepts to a non-technical audience, while the `agents.md` encodes them as instructions for AI agents to follow. A "good practices" section is planned for future development.
