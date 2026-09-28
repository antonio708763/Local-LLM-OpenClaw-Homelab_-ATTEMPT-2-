# Changelog

## 2026-09-28 — Requirements profile started

### Confirmed
- Previous hardware specifications remain current: RTX 4090 24 GB, Ryzen 9 7950X, 64 GB DDR5, Ubuntu/Windows dual boot.
- Local models will be the foundation and must remain usable without Internet access.
- Internet access is desired as an enhancement for current information and research.
- Multiple task-specific models are desired rather than a single universal model.
- Initial roles: general assistant, coding assistant, and uncensored/minimally restricted coding assistant.
- Long-term goal includes role-specific agents and specialized models.
- Assistants should eventually be able to act on authorized computers after requesting permission.
- Long-term device scope includes any explicitly authorized computer or phone.
- Preferred interface direction is a persistent desktop-friendly chat experience, with remote-device access later.
- Multimodal capability is a future goal.
- Moderate complexity is acceptable where it produces meaningful capability.
- The project will deliberately take the longer, educational route before implementation.

### Documentation
- Added `docs/01-local-ai-stack-reference.md`, mapping stack layers to both terminology and example application names.
- Added `docs/02-requirements-profile.md` to record the working requirements.

### Next
Teach the distinction between Internet-enabled local assistants and simple web-search tools, then move into hardware/inference fundamentals: GPU, VRAM, RAM, CPU, model sizes, precision, quantization, context, and how these constraints interact.

## 2026-09-27 — Attempt 2 started

### Status
Phase 0: Discovery and education.

### Decisions
- Restart the local-AI project from a clean slate.
- Use this repository as the source of truth for Attempt 2.
- Keep the previous repository available as historical/reference material.
- Do not assume the previous Ollama/OpenClaw architecture will be reused.
- Do not begin implementation until the desired system and requirements are understood.
- Explain terminology and present multiple options before major choices.

### Documentation
- Added the initial project README and clean-slate rules.
- Added `docs/00-ai-fundamentals.md` covering the first conceptual baseline: AI, ML, generative AI, LLMs, models, inference, tokens, parameters, runtimes, agents, tools, RAG, memory, quantization, VRAM, and possible homelab roles.

### Next
Continue Phase 0 by deciding what the local AI should actually do and what requirements matter most.
