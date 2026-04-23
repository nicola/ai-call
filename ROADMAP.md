# AI Call — Roadmap

## What is AI Call?

A structured AI-driven conversation where a user gets asked questions and gets to reply. The prompt defines the questions, depth, and when the conversation is done. The output is a clean markdown transcript.

**Core principle:** User data stays on the user's machine. Always.

---

## Phase 1: AI Agent Skill ✅

**Status:** Built — installed at `~/.pi/agent/skills/ai-call`

**Goal:** A skill that turns any AI agent into an interviewer.

**How it works:**
1. User invokes: *"Start an AI call about [prompt]"*
2. The prompt defines: questions to ask, areas to deep-dive, when to stop
3. The AI asks the first question
4. User replies (text or voice-to-text via their agent)
5. AI decides: follow-up on this answer, or move to next question
6. When done, generates a clean `ai-call-results-[timestamp].md` with Q&A pairs

**Key details:**
- Works with whatever AI the user is already running (Pi, Claude, Codex)
- No API keys needed — uses the agent's own model
- User can type or talk (voice input depends on the agent's capabilities)
- The prompt dictates the flow: number of questions, depth, when to wrap up
- Output is a markdown file with questions and answers, lightly formatted

**Deliverable:** Pi skill file at `skills/ai-call/SKILL.md`

---

## Phase 2: Local Desktop App

**Goal:** A native app for users without a local AI agent. Fully private, fully offline.

**How it works:**
1. Open the app
2. Load a prompt (paste text, open a file, or drag & drop)
3. Paste an API key (OpenAI, Anthropic, or Google) — stored locally
4. Answer questions with voice → transcribed locally
5. AI generates follow-up questions via API (browser/app → provider directly)
6. Download `results.md` when done

**Tech stack:** Tauri (like [Handy](https://github.com/cjpais/Handy))
- Small app (~5MB), native macOS (and cross-platform later)
- WKWebView — **no CORS issues**, can call any AI API directly
- Local Whisper model for transcription (bundled or downloaded on first run)
- No server needed, no data ever touches a third party except the AI provider the user chose
- UI built in HTML/JS/Tailwind (same code could be reused later)

**Why Tauri over a plain HTML file:**
- CORS: Anthropic blocks browser requests. Tauri's WebView bypasses this.
- File system: Save results directly to disk
- Audio: Native microphone access + local Whisper for transcription
- Distribution: Single `.dmg`, no `npx` or Python needed

**Deliverable:** macOS app (.dmg), later Windows/Linux

---

## Phase 3: Hosted Service (Deferred)

**Problem:** There's no good solution for the privacy/cost/friction trilemma:
- Frictionless (no install, no API key) requires running AI on a server → you see user data or you pay
- Fully private requires the user to bring their own AI → friction
- Google OAuth doesn't help: billing still goes to the app owner's GCP project

**Revisit when:**
- Browser-local models get good enough for follow-up generation (WebLLM, WebGPU)
- A provider offers a "sign in with your account" flow where the user's own quota is used
- There's a sustainable business model that justifies server costs

---

## Key Decisions

1. **Privacy is non-negotiable.** User data never touches our infrastructure.
2. **AI follow-ups are essential.** Pre-scripted questions are not enough.
3. **Two tiers of users:**
   - Pro users: have API keys, comfortable with tools → Skill (Phase 1) or App (Phase 2)
   - Non-technical users: need frictionless experience → Deferred until Phase 3 is solvable
4. **Tauri for the app** — small, native, no CORS, proven (Handy uses it).
5. **Transcription is local** — Web Speech API or Whisper, never sent to our servers.
