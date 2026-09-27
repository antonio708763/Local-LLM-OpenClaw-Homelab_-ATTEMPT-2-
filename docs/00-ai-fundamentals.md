# 00 — AI Fundamentals

## Purpose

This document records the conceptual baseline for Attempt 2 before any implementation decisions are made.

## The hierarchy

```text
Artificial Intelligence (AI)
└── Machine Learning (ML)
    └── Neural Networks / Deep Learning
        └── Generative AI
            └── Large Language Models (LLMs)
```

These terms overlap, but they are not interchangeable.

### Artificial intelligence

AI is the broad category of computer systems designed to perform tasks that normally require some form of human-like perception, language, reasoning, prediction, planning, or decision support.

### Machine learning

Machine learning is a way of creating AI systems by learning patterns from data instead of manually programming every rule.

### Neural network

A neural network is a mathematical model made of many adjustable numerical values. Modern LLMs use very large neural networks.

### Generative AI

Generative AI creates new output such as text, code, images, audio, or video based on patterns learned during training.

### Large language model

An LLM is a generative model designed primarily around language. It receives tokens as input and predicts tokens for its output.

## ChatGPT is more than a model

A useful mental model is:

```text
ChatGPT-like assistant
│
├── Model
├── Inference infrastructure
├── Conversation/interface layer
├── System instructions
├── Tools
├── Retrieval/search
├── Memory/context
├── Safety/permission systems
└── Product features
```

The model is a major component, but it is not the whole assistant.

A local project can reproduce many of these layers with separate self-hosted components.

## Tokens

Models do not directly process text as words in the same way humans read it.

Text is broken into smaller units called **tokens**.

A token might be:

- a whole short word;
- part of a longer word;
- punctuation;
- a number;
- whitespace or another text fragment.

The prompt and generated response are both represented as tokens.

## Parameters

**Parameters** are the learned numerical values inside a model.

Model names often contain values such as:

- 7B
- 14B
- 32B
- 70B

The **B** means billions of parameters.

More parameters usually require more memory and compute. A larger model is not automatically better for every task.

## Training vs inference

### Training

Training is the expensive process that creates or modifies a model by adjusting its parameters from large datasets.

### Inference

Inference is using an already-trained model to produce an answer.

For Attempt 2, the main goal is initially **local inference**, not training a foundation model from scratch.

## What "running AI locally" means

A local system generally means that model inference takes place on hardware under your control.

A simple local stack can look like:

```text
You
 ↓
Chat interface
 ↓
Inference runtime
 ↓
Model
 ↓
GPU / CPU / RAM
```

A more capable system can become:

```text
You
 ↓
UI / application
 ↓
Agent or assistant layer
 ├── memory
 ├── retrieval / RAG
 ├── web access
 ├── file access
 ├── shell / tools
 └── remote systems
 ↓
Inference runtime
 ↓
Local model
 ↓
Hardware
```

## Important layers

### Model

The trained neural network itself.

Examples will be evaluated later; no model family is selected yet.

### Model file / format

The stored representation of the model weights.

Examples of formats include GGUF and safetensors.

### Inference engine / runtime

Software that loads the model and performs inference.

Possible runtimes will be compared later. Ollama and llama.cpp are examples, but neither is selected yet.

### Front end / chat interface

The application used to talk to the model.

This can be a terminal, desktop app, browser UI, mobile client, or custom application.

### API

An API lets other software communicate with the inference server.

This is how one local AI server can potentially power multiple applications.

### Context window

The context window is the amount of tokenized information the model can actively consider during one request or conversation.

It is not the same thing as permanent memory.

### Memory

Memory is information stored outside the immediate model context so that an assistant can retrieve it later.

### RAG

**Retrieval-Augmented Generation (RAG)** means searching an external knowledge source and inserting relevant information into the model's context before it answers.

Possible sources include:

- documents;
- notes;
- manuals;
- configuration files;
- wikis;
- ticket history;
- source code.

### Embedding

An embedding is a numeric representation of meaning used to compare and search information semantically.

Embeddings are commonly used in RAG systems.

### Vector database

A vector database stores embeddings so information can be searched by semantic similarity rather than only exact keywords.

### Tool

A tool is an external capability made available to an AI system.

Examples:

- read a file;
- query an API;
- search documentation;
- execute a shell command;
- inspect a server;
- open a browser.

### Agent

An agent is a system that combines a model with tools and some logic for choosing actions.

The model alone does not automatically have control of a computer.

### Quantization

Quantization stores model weights using fewer bits.

Its goal is usually to reduce memory usage and increase practical inference speed.

The tradeoff is some loss of precision or model quality, depending on the quantization method.

### VRAM

VRAM is memory on the GPU.

For local LLMs, VRAM is often one of the most important hardware limits because model weights and working data may need to fit there.

### RAM

System RAM can also hold model data and context, and some runtimes can split work between RAM/CPU and VRAM/GPU.

### GPU offload

GPU offload means moving some or all model computation to the GPU.

### Fine-tuning

Fine-tuning modifies a model by training it further on a narrower dataset or objective.

This is different from simply prompting it or giving it documents through RAG.

### Base model vs instruct/chat model

A **base model** is primarily trained to continue text.

An **instruct** or **chat** model has additional training intended to make it follow instructions and hold conversations more effectively.

### Multimodal

A multimodal model can work with more than one kind of input or output, such as text plus images, audio, or video.

## Why local AI can be useful

Potential advantages:

- privacy and local control;
- offline availability;
- no per-request cloud API cost;
- ability to experiment with many models and runtimes;
- deeper control over configuration;
- integration with a homelab and local files;
- ability to build specialized assistants;
- reduced dependence on one hosted provider.

Potential disadvantages:

- local models may be weaker than top cloud models;
- hardware limits model size and context;
- setup and maintenance become your responsibility;
- GPU power draw and heat can be significant;
- agents with system access introduce security risk;
- model and runtime ecosystems change quickly.

## Possible roles in this homelab

These are options, not requirements.

### A. Private local chatbot

A ChatGPT-like interface for normal questions and brainstorming.

### B. Coding assistant

Generate, explain, review, and debug code or configuration.

### C. Homelab copilot

Read documentation and configuration, explain errors, analyze logs, and recommend changes.

### D. Documentation assistant

Search and answer questions over personal notes, manuals, Git repositories, and project documentation.

### E. Controlled agent

Use tools to take approved actions such as reading files, running commands, editing configuration, or operating remote lab systems.

### F. Local AI service

Expose one or more local models through an API so desktops, laptops, web interfaces, scripts, and other applications can use the same AI server.

### G. Multimodal assistant

Later add image understanding, screenshots, voice, speech-to-text, text-to-speech, or other media.

## Phase 0 requirement

No implementation choice should be made just because it was used in the previous project.

We will first determine:

1. what jobs the system should perform;
2. where it should run;
3. how private/offline it must be;
4. how much computer access it should receive;
5. what user interfaces are desired;
6. what performance is acceptable;
7. what level of maintenance and complexity is acceptable.

Only then will candidate architectures be designed and compared.
