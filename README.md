# Coral Multi-Agent System Setup Guide

This repo provides a step-by-step guide to build and run a complete **multi-agent system** using [Coral Protocol](https://github.com/Coral-Protocol), open-source agents, and Coral Studio.

You’ll go from scratch to a fully working setup with:
- Coral Server
- Coral Studio (UI)
- Multiple connected agents
- Live sessions and outputs

---

## Guide Overview

| Step | File | Description |
|------|------|-------------|
| 1️⃣ | [introduction.md](./introduction.md) | What is Coral? What will you build? |
| 2️⃣ | [pre-requisites.md](./pre-requisites.md) | Tools to install before starting |
| 3️⃣ | [setup-coral-studio.md](./setup-coral-studio.md) | Clone and run the Coral Studio UI |
| 4️⃣ | [setup-coral-server.md](./setup-coral-server.md) | Set up and start Coral Server backend |
| 5️⃣ | [choose-agent.md](./choose-agent.md) | Browse and select open-source agents |
| 6️⃣ | [configure-agents.md](./configure-agents.md) | Add agent definitions to application.yaml |
| 7️⃣ | [start-server-and-create-session.md](./start-server-and-create-session.md) | Start the server & create a session |
| 8️⃣ | [run-agent.md](./run-agent.md) | Run one or more agents in separate terminals |

---

## Key Components

- **Coral Server** — Agent runtime & messaging backend  
- **Coral Studio** — UI to create sessions and connect agents  
- **application.yaml** — Your config file to define agents 
---

## Open-Source Coral Repos

- [Coral Server](https://github.com/Coral-Protocol/coral-server)  
- [Coral Studio](https://github.com/Coral-Protocol/coral-studio)  
- [Agent Registry](https://github.com/Coral-Protocol/awesome-agents-for-multi-agent-systems)  

---

## UI Exploration

We also explored the Coral debug UI. It currently focuses on session debugging, so we used Postman for input testing, which worked smoothly.

![Creating thread in coral-dbg](./assets/gifs/creating_thread.gif)

> The UI allows thread creation for active sessions, but interaction remains limited. Postman was used for input/output testing.
