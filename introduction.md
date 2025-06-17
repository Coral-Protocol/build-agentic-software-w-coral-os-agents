# Coral Multi-Agent System Setup Guide

Welcome! This guide helps you set up a fully working **multi-agent system** using open-source agents from the **Coral Protocol** ecosystem.

You’ll go from a scratch to running live agents that collaborate using Coral Server and Coral Studio — step by step.

---

## What is Coral?

**Coral Protocol** is an open-source framework for building intelligent, modular **multi-agent systems**.

It gives developers a way to:
- Define agents that communicate and collaborate
- Manage agent sessions and workflows via a central server
- Interact with agents using a visual UI (Coral Studio)
- Connect multiple agents (including LLM-powered ones) into a task-solving network

---

## What Will You Build?

By the end of this guide, you’ll have:

A fully working local Coral setup with:
- **Coral Server** running on your machine  
- **Coral Studio** UI running in your browser  
- **Two or more open-source agents** connected and ready  
- A session where agents **communicate, take actions, and return results**

You’ll be able to:
- Create sessions via the UI or Postman
- Route messages between agents using structured threads
- Extend or replace agents based on your needs

---

## What Makes Coral Different?

- **Structured agent collaboration** using threads, not just plain text
- **Plug-and-Interact open-source agents** — no need to build from scratch
- **Privacy-focused architecture** — agents run in isolated, scoped sessions
- **UI + API support** — test with Coral Studio or Postman

---

## What You'll Use

In this guide, you'll work with:

| Component       | Purpose                                     |
|----------------|---------------------------------------------|
| Coral Server    | Runs your agents and manages communication |
| Coral Studio    | UI to manage agents, sessions, and input   |
| Open-source Agents | Ready-to-use building blocks               |
| application.yaml| Agent config + runtime definitions         |

---

## Open-Source Coral Components

| Component      | Link |
|----------------|------|
| Coral Server   | [coral-server](https://github.com/Coral-Protocol/coral-server) |
| Coral Studio   | [coral-studio](https://github.com/Coral-Protocol/coral-studio) |
| Agent Registry | [awesome-agents-for-multi-agent-systems](https://github.com/Coral-Protocol/awesome-agents-for-multi-agent-systems) |

---

## What You’ll Do Next

In the next steps, you’ll:

1. Install prerequisites (Python, Node, etc.)
2. Set up Coral Studio and Coral Server
3. Choose and configure your agents
4. Run everything and create a working session
5. Get output and test multi-agent collaboration
