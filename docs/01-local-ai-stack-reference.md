# 01 — Local AI Stack Reference

This document is a quick reference for identifying **what category a piece of software belongs to**.

The most important idea:

> A local AI system is a stack of separate parts. A model is not the same thing as the software that runs it, and neither is necessarily the same thing as the program used to chat with it.

## The stack

```text
┌─────────────────────────────────────────────┐
│ 1. USER INTERFACE / CHAT PROGRAM            │
│    What you look at and type into           │
├─────────────────────────────────────────────┤
│ 2. ASSISTANT / AGENT LAYER                  │
│    Tools, permissions, workflows, actions   │
├─────────────────────────────────────────────┤
│ 3. MEMORY / RAG / KNOWLEDGE                 │
│    Documents and information retrieval      │
├─────────────────────────────────────────────┤
│ 4. API / SERVER INTERFACE                   │
│    How programs talk to the AI backend      │
├─────────────────────────────────────────────┤
│ 5. INFERENCE RUNTIME / ENGINE               │
│    Software that loads and runs the model   │
├─────────────────────────────────────────────┤
│ 6. MODEL                                    │
│    The trained neural network               │
├─────────────────────────────────────────────┤
│ 7. HARDWARE                                 │
│    GPU, VRAM, CPU, RAM, storage             │
└─────────────────────────────────────────────┘
```

Not every setup has a separate product at every layer. Some applications combine several layers.

## Layer 1 — User interface / chat program

This is the part the user actually interacts with.

Possible forms:

- desktop application;
- browser interface;
- terminal;
- phone application;
- Discord-like chat interface;
- IDE extension.

Examples of software that can provide or include an interface:

- Open WebUI;
- LM Studio;
- AnythingLLM;
- SillyTavern;
- command-line interfaces;
- custom web or desktop applications.

Important: an interface may also bundle other layers. The category describes its role, not necessarily everything the application can do.

## Layer 2 — Assistant / agent layer

This layer gives the model more than conversation.

Possible capabilities:

- tools;
- shell access;
- file access;
- browser control;
- remote-computer access;
- approval rules;
- workflows;
- task planning;
- multiple specialized agents.

Examples include:

- OpenClaw;
- coding-agent applications;
- other agent frameworks.

A model does **not** automatically become an agent just because it is capable of writing commands.

## Layer 3 — Memory / RAG / knowledge

This layer helps an assistant use information that is not permanently inside the model.

Examples:

- project documentation;
- manuals;
- configuration files;
- code repositories;
- notes;
- conversation summaries;
- troubleshooting history.

RAG means **Retrieval-Augmented Generation**: retrieve relevant information first, then give it to the model as part of the current context.

This layer may use:

- embeddings;
- semantic search;
- vector databases;
- normal keyword search;
- a combination of methods.

## Layer 4 — API / server interface

An API is the communication boundary between applications.

Example:

```text
Desktop UI
    │
    ├── API request
    ▼
Local AI server
    │
    ▼
Model
```

If the local backend exposes a compatible API, several clients may be able to use the same AI server.

This is important for the long-term goal of authorized desktops, laptops, phones, and homelab systems using the same local-AI foundation.

## Layer 5 — Inference runtime / engine

This is the software that actually executes the model.

Its jobs can include:

- loading model weights;
- allocating VRAM and RAM;
- sending computation to the GPU or CPU;
- managing context;
- generating tokens;
- exposing an API;
- handling model files.

Examples:

- Ollama;
- llama.cpp;
- vLLM;
- other inference engines.

These products differ substantially in ease of use, supported hardware, model formats, performance controls, server features, and complexity.

No runtime is selected yet.

## Layer 6 — Model

The model is the trained neural network itself.

Examples of model families include:

- Qwen;
- Llama;
- Gemma;
- Mistral;
- DeepSeek;
- Dolphin-family fine-tunes and derivatives;
- many specialized coding, reasoning, vision, and general-purpose models.

A model can have different variants:

- parameter sizes;
- instruct/chat versions;
- coding versions;
- reasoning versions;
- quantizations;
- fine-tunes;
- multimodal versions.

The project intends to support multiple models selected according to the task.

## Layer 7 — Hardware

The physical machine performing the computation.

Confirmed workstation:

- NVIDIA RTX 4090 — 24 GB VRAM
- AMD Ryzen 9 7950X
- 64 GB DDR5 RAM
- Ubuntu / Windows dual boot

Important hardware terms:

- **GPU:** processor especially useful for highly parallel AI computation.
- **VRAM:** memory directly attached to the GPU.
- **CPU:** general-purpose processor.
- **RAM:** normal system memory.
- **Storage:** where models, applications, databases, logs, and documents live.

## Example 1 — A simple local chatbot

```text
Open WebUI             ← interface
        ↓
Ollama                 ← runtime / server
        ↓
Qwen model             ← model
        ↓
RTX 4090               ← hardware
```

This is an example only, not the selected architecture.

## Example 2 — Same model, different interface

```text
LM Studio              ← interface + runtime features
        ↓
Qwen model
        ↓
RTX 4090
```

The user experience can change even if the underlying model family is similar.

## Example 3 — Agent system

```text
Desktop / browser UI
        ↓
OpenClaw               ← agent / tools / permissions
        ↓
local inference API
        ↓
runtime
        ↓
coding model
        ↓
RTX 4090
```

Here OpenClaw is not the model and is not the GPU runtime. It is an additional control/agent layer.

## Example 4 — Multiple models behind one system

```text
                     User
                      │
               Main interface
                      │
              Agent / router layer
        ┌─────────────┼──────────────┐
        │             │              │
        ▼             ▼              ▼
 General model   Coding model   Uncensored coding model
        │             │              │
        └─────────────┴──────────────┘
                      │
                 runtime(s)
                      │
                  RTX 4090
```

This is close to one of the current project goals, but the software used for each layer is still undecided.

## Shortcut for identifying software

When a new application name appears, ask:

1. **Do I type messages into it?**  
   It may be an interface.

2. **Does it load model weights and use my GPU?**  
   It may be an inference runtime.

3. **Is it the actual trained neural network?**  
   It is a model.

4. **Does it give the AI tools, permissions, or computer control?**  
   It may be an agent layer.

5. **Does it store/search documents or past information?**  
   It may be a RAG or memory component.

6. **Does it do several of these at once?**  
   It is probably an integrated application combining multiple layers.

This classification method is more useful than trying to memorize every product name.
