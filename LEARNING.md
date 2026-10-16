# LEARNING.md: progress and handoff

Read this first in any new session, on any laptop. It holds everything needed to continue.

## Who I am and how to teach me

- I'm Abhishek. I work at an AI company that sells a **SaaS voice-agent platform for banks**. The platform is built and in the integration phase. No bank is live yet, so there's **no real bank customer data**, only our own test calls.
- Our stack is LiveKit Agents (Python), self-hosted. Transcripts and recordings of test calls are saved.
- I know nothing about evals yet. I learn by building.

**Teaching rules:**
- **I write all the code myself.** Tell me what to type, where, and why; I type it, show you, and you review. Don't edit my company code.
- Keep replies **very short**: one small step per reply, then stop and wait.
- Explain from basics in plain words. Explain every piece of jargon the first time it appears.
- Readable code: plain `for` loops, named variables, no one-liners. Put a `#` comment above each line.
- Every best practice must come from a real engineering blog or OSS project, with a link. Mark your own ideas as `[INFERENCE]`. Never make things up.
- If I get something wrong, tell me what and why, and let me fix it.

## Our two must-never rules

1. Guardrails are never broken.
2. Answers always match the bank's knowledge base (KB).

## Study material in this repo

| File | What |
|---|---|
| `IMPLEMENTATION_BLUEPRINT.md` | How industry builds the eval system, mapped onto our platform, with a build order |
| `PRACTICAL_ROADMAP.md` | 9 learning stages and 20 best practices, each tied to a real company + OSS code |
| `SOURCES.md` | Every source, with a phrase to search for so each claim can be checked |
| `lessons/` | Saved lessons |
| `ROADMAP.md` | Theory map and glossary |

## Progress

- [x] Lesson 1: What is an eval? (`lessons/01-what-is-an-eval.md`)
- [ ] Lesson 2: Read your calls (`lessons/02-read-your-calls.md`). Homework not done yet
- [ ] Adapt `IMPLEMENTATION_BLUEPRINT.md` to our real codebase (needs the 8 answers below)

## Next step

On the company laptop, read our agent's codebase (read-only) and answer:

1. `livekit-agents` version; STT / LLM / TTS providers
2. Names of the agent's tools, one line each
3. How guardrails are implemented, and where
4. How the KB works (retrieval method, store, are retrieved passages logged?)
5. Where and how test-call transcripts/recordings are saved, and in what format
6. Do saved transcripts include tool calls and their results?
7. Existing tests and CI
8. Field names of one saved transcript (fake values only)

Then explain how `IMPLEMENTATION_BLUEPRINT.md` maps onto our code. After that, continue with Lesson 2 using our real test-call transcripts.
