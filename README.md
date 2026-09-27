# Local LLM + OpenClaw Homelab — Attempt 2

I'll be brainstorming with AI instead of playing it by ear.

A clean-slate project for learning, designing, and eventually building a local AI system.

## Current phase

**Phase 0 — Discovery and education**

No AI runtime, model, agent framework, remote-control system, or architecture has been selected yet.

The goal of this phase is to understand the available choices before installing or changing anything.

## Project rules

1. **Learn before building.** Explain the concepts and terminology before implementation.
2. **Present options before choosing.** Do not assume Ollama, llama.cpp, OpenClaw, a particular model, or any other component is automatically the right choice.
3. **Ask questions.** Important design decisions should come from stated requirements rather than guesses.
4. **Document progress.** This repository is the source of truth for Attempt 2.
5. **Keep the old project as historical reference only.** Useful lessons can be reused, but old architectural choices are not automatically carried forward.
6. **No implementation during Phase 0.** We will not install or configure the local AI stack until the desired system is clearly defined.
7. **Prefer reversible choices.** Later implementation should favor backups, rollback paths, isolated testing, and documented validation.

## Historical reference

Previous project:

https://github.com/antonio708763/local-llm-openclaw-homelab

The previous project included Ollama, OpenClaw, local Qwen models, Forge/Power profiles, Docker sandboxing, remote-node control, context optimization, and memory experiments.

Those are now reference material, not current design decisions.

## Known historical hardware

The previous repository documented:

- NVIDIA RTX 4090 — 24 GB VRAM
- AMD Ryzen 9 7950X
- 64 GB DDR5 RAM
- Ubuntu / Windows dual boot

These specifications will be reconfirmed before implementation.

## Questions Attempt 2 must answer

Before building anything, the project will explore:

- What is AI, machine learning, generative AI, and an LLM?
- What exactly is a model?
- What does "running a model locally" mean?
- What jobs should the local AI actually perform?
- Which tasks should remain local and which, if any, may use cloud services?
- What hardware resources matter: GPU, VRAM, CPU, RAM, storage, and power?
- How model size, parameters, quantization, context length, and tokens affect quality and speed.
- The difference between a model, inference engine/runtime, chat interface, API, agent framework, tools, RAG, memory, and automation.
- Whether to use Ollama, llama.cpp, vLLM, another runtime, or more than one.
- Whether OpenClaw is appropriate, optional, or unnecessary.
- Which model families are suitable for general chat, coding, homelab administration, research, vision, and other tasks.
- How much autonomy the system should have.
- What security and permission model is appropriate.
- How local clients and remote devices should connect.
- How to benchmark candidate models and runtimes before committing.
- How to keep the system maintainable, understandable, and recoverable.

## Current objective

Start with the fundamentals and build a requirements profile.

Only after the requirements profile is complete will we design candidate architectures and compare them.

## Next discussion

1. AI fundamentals and terminology.
2. What local AI can and cannot do.
3. Possible roles for AI in this homelab.
4. Requirements questionnaire.
5. Candidate architecture families.
6. Evaluation and testing plan.
7. Implementation only after a design is selected.
