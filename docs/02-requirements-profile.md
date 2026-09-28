# 02 — Requirements Profile

## Status

This is the current requirements profile for Attempt 2. It is a working document and will change as the project becomes better understood.

## Confirmed hardware

- NVIDIA RTX 4090 — 24 GB VRAM
- AMD Ryzen 9 7950X
- 64 GB DDR5 RAM
- Ubuntu / Windows dual boot

## Core philosophy

- Local models are the foundation.
- The system should remain useful without Internet access.
- Internet access is desirable when it improves freshness, research, or capability.
- The project should be methodical rather than rushed.
- Major choices should be compared before selection.
- The architecture should be taught and understood rather than treated as a black box.
- Moderate complexity is acceptable when it provides meaningful capability.
- Implementation should not begin until the architecture and requirements are understood well enough to avoid repeating Attempt 1.

## Model strategy

The system should support multiple models for different jobs rather than force one model to do everything.

Initial desired roles:

1. General ChatGPT-like assistant.
2. Coding assistant.
3. Uncensored / minimally restricted coding assistant, with Dolphin-style models noted as one example to evaluate.
4. Later, more specialized models and role-specific agents.

No specific model is selected yet.

## Connectivity

### Offline baseline

Core model inference should work locally without the Internet.

### Online enhancement

When Internet is available, assistants should be able to use it to improve answers with current information.

The exact Internet-access architecture is not selected yet.

## Action model

Desired long-term permission behavior:

- assistants may use tools and interact with systems;
- actions should require user approval before execution;
- authorization and impact levels will need a more detailed policy later.

## Device scope

Long-term goal:

- workstation;
- laptops;
- phones;
- homelab servers;
- eventually any explicitly authorized device.

The design should avoid assuming that all AI computation must happen on every client device. A central local AI server with remote clients is one architecture to evaluate.

## User interface

Preferred direction:

- a primary desktop-friendly conversational interface;
- ideally a persistent chat experience comparable in feel to Discord or other modern messaging applications;
- later accessible from authorized laptops and phones.

The interface software is not yet selected.

## Multimodal direction

Eventually support more than text.

Possible future capabilities:

- screenshots and images;
- documents and PDFs;
- speech-to-text;
- text-to-speech;
- voice conversation;
- possibly other media.

Multimodal capability is a later phase, not a requirement for the first working text stack.

## Complexity preference

Current target:

**Moderate complexity for meaningful capability.**

The project may go deeper when there is a concrete benefit, but low-level complexity should not be added simply for its own sake.

## Learning requirement

Learning is a primary project requirement, not incidental documentation.

Before major implementation decisions:

1. explain the layer involved;
2. teach the important terminology;
3. identify realistic alternatives;
4. explain tradeoffs;
5. relate those tradeoffs to the actual hardware and goals;
6. ask requirement questions where the answer changes the architecture;
7. record the decision and reasoning.

## Current unresolved design questions

- Should the main interface be a dedicated desktop application, local web application, or a web application installed like a desktop app?
- Should the system use one inference runtime or multiple runtimes?
- How should models be switched or routed by task?
- Should model routing be manual initially and automated later?
- What agent framework, if any, should be used?
- How should approval prompts work for computer actions?
- How should authorized remote devices connect?
- How much Internet access should be delegated directly to an agent versus exposed as specific tools?
- How should local memory and RAG be designed?
- Which multimodal capabilities belong in the first expansion phase?
- How much of the system should run as persistent background services?
