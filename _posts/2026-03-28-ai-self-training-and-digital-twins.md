---
layout: post
title: "AI That Trains Itself — And Builds a Copy of You"
date: 2026-03-28
categories: [AI]
tags: [self-training, digital-twins, autoresearch, agents, self-improvement]
author: Ark Newsletter
---

## Summary

An AI ran 50 experiments overnight, improved its own training code, and committed the results — no human involved. Meanwhile, startups are racing to build digital twins that replicate how you think, write, and make decisions at work. These two trends are converging. Here is what is happening and why you should pay attention.

## The AI That Improves Itself While You Sleep

In early March, Andrej Karpathy released [Autoresearch](https://github.com/karpathy/autoresearch) — a minimal framework where an AI agent autonomously improves a neural network's training code. The entire system is three files. One defines the model. One defines the rules. The agent modifies the training code, runs an experiment, checks if the result improved, and either keeps or discards the change. Then it repeats. Indefinitely.

The design philosophy is almost comically simple:

- **One editable file** (`train.py`) — the agent can only modify this
- **One metric** (`val_bpb`) — lower is better, no ambiguity
- **Five-minute budget** per experiment — fast iteration, no wasted compute
- **Git as the lab notebook** — every experiment is a commit

In the initial demo, the agent ran 50 experiments overnight and discovered improved learning rates and architectural tweaks that a human researcher might have taken days to find. The repository hit 21,000 stars within a week. An [Apple Silicon port](https://github.com/trevin-creator/autoresearch-mlx) appeared within days. Karpathy's announcement racked up 8.6 million views.

What matters here is not the specific ML improvements. It is the *pattern*: define a clear metric, give an agent a small configuration surface, and let it run unsupervised. This pattern generalizes far beyond neural network training.

## The Self-Improvement Landscape

Autoresearch did not appear in a vacuum. A wave of self-training research is redefining how AI systems get better.

**Meta's SPICE** (Self-Play in Corpus Environments) splits a single model into two roles — a Challenger that mines documents to create reasoning tasks, and a Reasoner that solves them without seeing the source. The information asymmetry creates a natural curriculum at the frontier of capability. Results: +8.9% on math benchmarks, +9.8% on general reasoning.

**OpenAI's Self-Evolving Agents Cookbook** lays out a production retraining loop: an agent executes tasks, human review and LLM judges generate feedback signals, and improved prompts are deployed back. The key insight is that agents plateau after proof-of-concept because they depend on humans to diagnose edge cases. Automating the diagnosis closes the loop.

**Microsoft STOP** (Self-Taught Optimizer) takes it further — an "improver" program applies itself to improve *its own code*. Starting from a simple seed, it independently discovers beam search, genetic algorithms, and simulated annealing. The underlying model weights never change; all improvement happens at the scaffolding level.

**DeepSeek GRPO** demonstrates that simpler reinforcement learning algorithms can match PPO performance at lower compute cost, making self-improvement loops cheaper to run.

The common thread: AI systems that get better without waiting for humans to intervene.

## Your Digital Twin Is Coming

While self-training research focuses on making AI smarter, a parallel movement is making AI more *personal* — building replicas of individual people from their workplace data.

**Read AI's "Ada"**, launched in February 2026, monitors your inbox, schedules meetings, and answers questions using your company knowledge base and meeting history. It does not wait for commands — it jumps in when it detects an opportunity to help. Currently email-only, expanding to Slack and Teams.

**Sentience**, founded by an ex-Amazon engineer with $6.5 million from Bain Capital Ventures, ingests your emails, Slack messages, Apple Notes, and social media to create a chatbot that mimics your tone, opinions, and writing quirks. The long-term vision: a digital twin that recalls anything you have experienced and operates on your behalf.

**Personal.ai** takes a different approach with Personal Language Models (PLMs) — small models trained exclusively on an individual's "Memory Stack." They can be retrained in minutes as new knowledge is added. The company claims 50-75% gains in speed, accuracy, and consistency for enterprise knowledge work.

**IgniteTech's MyPersonas**, showcased at CES 2026, creates AI replicas of employees using video, voice, and written materials — digital stand-ins that answer questions and chat on video in 160 languages.

The market signal is clear: personalized AI is moving from novelty to infrastructure.

## Where Self-Training Meets Digital Twins

Here is where it gets interesting. Combine Autoresearch's improvement loop with a digital twin, and you get a system that not only replicates how you think — but gets better at it autonomously.

The architecture looks like this:

**Layer 1 — Data extraction.** Pull decisions from Slack threads, GitHub PR reviews, Jira triage, and Confluence pages. Normalize everything into a unified timeline of "this person faced this situation and made this choice."

**Layer 2 — Persona construction.** Build a system prompt from extracted patterns: communication style, decision-making principles, domain expertise, recent context. Add a RAG layer backed by a vector database of historical decisions. At inference time, the twin retrieves your most relevant past decisions to inform new ones.

**Layer 3 — Autoresearch-style improvement.** Define a clear metric (decision similarity between the twin and the real person). Let an agent modify the persona configuration — adjust the system prompt, tune RAG parameters, refine decision-extraction rules. Run evaluation against held-out decisions. Keep improvements, discard regressions. Repeat overnight.

The evaluation uses an LLM-as-judge scoring five dimensions: decision alignment, reasoning alignment, tone match, prioritization alignment, and action specificity. A temporal train/validation split (train on past data, evaluate on recent decisions) mimics real-world deployment.

Expected throughput: ~30 experiments per hour, ~240 overnight. Each experiment takes about 2 minutes of LLM inference — far faster than Autoresearch's 5-minute GPU training runs.

The beauty of this approach is that you start simple (just a well-crafted prompt) and the system discovers what it needs to add. No fine-tuning required until the evaluation framework proves the simpler approaches are insufficient.

## Why This Matters Now

Three trends are converging to make this practical today:

1. **The tools exist.** MCP at 97 million monthly installs means the connective tissue between AI and workplace data is already production-ready. Extracting decisions from Slack, GitHub, Jira, and Confluence is an API call, not a research project.

2. **Self-improvement loops work.** Autoresearch, SPICE, and the OpenAI Cookbook have proven that automated experiment loops reliably find improvements. The pattern is domain-agnostic.

3. **The economics work.** A prompt-based persona with RAG costs essentially nothing to build. The improvement loop runs on standard LLM inference. No GPUs, no fine-tuning, no MLOps team required.

The implication: within months, not years, the question will shift from "Can we build a digital twin?" to "How accurate is yours?"

## Key Takeaways

1. **Self-improvement is a design pattern, not a research frontier.** Autoresearch proved that a three-file system can autonomously improve AI performance overnight. The pattern — clear metric, small configuration surface, automated experiment loop — transfers to any domain with measurable quality.

2. **Digital twins are going from demo to product.** Read AI, Sentience, and Personal.ai are shipping real products that replicate individual work styles. The workplace data to build these twins is already captured in tools you use daily.

3. **The combination is the unlock.** A digital twin that improves itself by running overnight experiments against your real decision history is not science fiction — it is an engineering project with known components. The question is who builds it first.

---

*The Ark Newsletter covers developments in AI that matter — not the hype, but the signal. See something we should cover? Let us know.*
