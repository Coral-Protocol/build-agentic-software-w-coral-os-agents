# Coral Multi-Agent System Setup Guide

This repo provides a step-by-step guide to build and run a complete **multi-agent system** using [Coral Protocol](https://github.com/Coral-Protocol), open-source agents, and Coral Studio.

You’ll go from scratch to a fully working setup with:
- Coral Server
- Coral Studio (UI)
- Multiple connected agents
- Live sessions and outputs

---

## Guide Overview

| Step | Section | Description |
|------|---------|-------------|
| 1️⃣ | [Introduction](#introduction) | What is Coral? What will you build? |
| 2️⃣ | [Prerequisites](#prerequisites) | Tools to install before starting |
| 3️⃣ | [Set Up Coral Studio](#set-up-coral-studio-ui) | Clone and run the Coral Studio UI |
| 4️⃣ | [Set Up Coral Server](#set-up-coral-server-backend) | Set up and start Coral Server backend |
| 5️⃣ | [Choose Your Agent](#choose-your-agent) | Browse and select open-source agents |
| 6️⃣ | [Configure Agent Definitions](#configure-agent-definitions) | Add agent definitions to application.yaml |
| 7️⃣ | [Start Coral Server & Create a Session](#start-coral-server--create-a-session) | Start the server & create a session |
| 8️⃣ | [Run the Agent](#run-the-agent) | Run one or more agents in separate terminals |

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

## Introduction

Welcome! This guide helps you set up a fully working **multi-agent system** using open-source agents from the **Coral Protocol** ecosystem.

You'll go from a scratch to running live agents that collaborate using Coral Server and Coral Studio — step by step.

### What is Coral?

**Coral Protocol** is an open-source framework for building intelligent, modular **multi-agent systems**.

It gives developers a way to:
- Define agents that communicate and collaborate
- Manage agent sessions and workflows via a central server
- Interact with agents using a visual UI (Coral Studio)
- Connect multiple agents (including LLM-powered ones) into a task-solving network

### What Will You Build?

By the end of this guide, you'll have:

A fully working local Coral setup with:
- **Coral Server** running on your machine  
- **Coral Studio** UI running in your browser  
- **Two or more open-source agents** connected and ready  
- A session where agents **communicate, take actions, and return results**

You'll be able to:
- Create sessions via the UI or Postman
- Route messages between agents using structured threads
- Extend or replace agents based on your needs

### What Makes Coral Different?

- **Structured agent collaboration** using threads, not just plain text
- **Plug-and-Interact open-source agents** — no need to build from scratch
- **Privacy-focused architecture** — agents run in isolated, scoped sessions
- **UI + API support** — test with Coral Studio or Postman

### What You'll Use

In this guide, you'll work with:

| Component       | Purpose                                     |
|----------------|---------------------------------------------|
| Coral Server    | Runs your agents and manages communication |
| Coral Studio    | UI to manage agents, sessions, and input   |
| Open-source Agents | Ready-to-use building blocks               |
| application.yaml| Agent config + runtime definitions         |

### Open-Source Coral Components

| Component      | Link |
|----------------|------|
| Coral Server   | [coral-server](https://github.com/Coral-Protocol/coral-server) |
| Coral Studio   | [coral-studio](https://github.com/Coral-Protocol/coral-studio) |
| Agent Registry | [awesome-agents-for-multi-agent-systems](https://github.com/Coral-Protocol/awesome-agents-for-multi-agent-systems) |

### What You'll Do Next

In the next steps, you'll:

1. Install prerequisites (Python, Node, etc.)
2. Set up Coral Studio and Coral Server
3. Choose and configure your agents
4. Run everything and create a working session
5. Get output and test multi-agent collaboration

---

## Prerequisites

Before you set up and run Coral, make sure your local environment has the following tools installed.

These are required to run agents, Coral Server, Coral Studio, and external LLMs like OpenAI.

### Required Tools & Versions

| Tool | Version | Why You Need It |
|------|---------|------------------|
| **Python** | 3.10+ | Needed for most agents (especially LangChain-based) |
| **uv** | latest | Python environment & dependency manager (`pip install uv`) |
| **Node.js** | 18+ | Required to run Coral Studio (the UI) |
| **npm** | Comes with Node | Used to install and run Studio dependencies |
| **Java (JDK)** | 17+ | Some agents require JVM support |
| **Git** | latest | To clone agent and Coral repos |
| **OpenAI API Key** | Any | Needed for agents using OpenAI models (GPT) |
| **Postman** (optional) | latest | For testing Coral Server API directly |
| **curl** (optional) | Any | CLI alternative to Postman for testing API calls |

### Recommended Tools

| Tool | Reason |
|------|--------|
| **Anaconda** | Easy Python env management (optional but useful) |
| **Git Bash** (Windows) | Better than PowerShell for running shell commands |
| **Visual Studio Code** | IDE for editing agent code and config |
| **`.env` file support** | Use for storing API keys securely |

### Environment Variables You'll Need

These are typically set in a `.env` file or passed into agents via `application.yaml`:

```env
OPENAI_API_KEY=sk-xxxxxxxxxxxxxxxxxxxxxx
GITHUB_PERSONAL_ACCESS_TOKEN=ghp-xxxxxxxxxxxx
LINKUP_API_KEY=linkup-xxxxxxxxxxxx
```

---

## Set Up Coral Studio (UI)

**Coral Studio** is a web-based UI for managing sessions, agents, and threads visually.

This step walks you through installing and running Coral Studio locally on your machine.

### 1. Run coral studio

Open your terminal (Git Bash or PowerShell) and run:

```bash
docker run -p 3000:3000 ghcr.io/coral-protocol/coral-studio
```

This will start the Studio UI at:
```
http://localhost:3000
```
Open this URL in your web browser to access the Coral Studio interface.

### 2. Confirm It's Working
You should see:
- A dashboard for Coral Studio
- An option to create a session or connect to Coral Server
- A visual interface to observe and interact with threads and agents

[//]: # (Coral-UI should look like this)

[//]: # (<img width="957" alt="Image" src="https://github.com/user-attachments/assets/819ce48e-b740-459f-a0aa-9eb23ec66c1f" />)

---

## Run the coral server

**Coral Server** is the engine that runs your multi-agent sessions, executes agent logic, and facilitates communication between agents.

In this step, you'll set up and start Coral Server locally using your own `application.yaml` config.

### 1. Run the Coral Server from Docker

First we will create a temporary application.yaml file which we will later populate with our agents.

```bash
mkdir config
touch application.yaml # create an empty application.yaml file
```

```bash
docker run --name coral-server -p 5555:5555 -v ./application.yaml:/config coral-server
```

This will launch the server,
which acts as a control pane that creates instances of agents
connected to their individualised MCP servers allowing them to communicate and collaborate.


---

## Choose Your Agent

Before building a multi-agent system, we need to decide **what kind of task our agent will perform**. With **Coral**, you can pick from a list of existing agents OR write your own.

Coral supports a modular approach using agents and in our case, we are using an **Interface Agent**, which wraps powerful tools like LangChain, OpenAI.

### What is an Agent?

An agent is simply:
- A Python (or other) script
- That follows a communication protocol
- And can be called by Coral to perform tasks

### Choose Agents from Coral Awsome Agents

Visit the official Coral community list:

- [Awsome Agents for Multi-agent systems](https://github.com/Coral-Protocol/awesome-agents-for-multi-agent-systems)

  <img width="467" alt="Image" src="https://github.com/user-attachments/assets/07fc07cf-8f32-407c-9252-cca6277d4043" />

From there, pick one. For this tutorial, we're using:

### Choose Agents for Your Use Case

Pick 1–3 agents depending on your goal.

Example setup:

| Agent ID | Description |
|----------|-------------|
| `coral-interface` | An interface agent that coordinates actions |
| `coral-research` | Performs deep research using LLM + tools |
| `coral-repo` | Analyzes GitHub repos using LangChain |

You can mix & match based on what you're trying to build.

### Copy Agent Snippets (YAML Format)

Each agent in the registry provides a snippet like this:

```yaml
coral-interface:
  options:
    - name: "OPENAI_API_KEY"
      type: "string"
      description: "OpenAI Key"
  runtime:
    type: "executable"
    command:
      - "bash"
      - "-c"
      - "cd ../Coral-Interface-Agent && uv sync && uv run python 0-langchain-interface.py"
    environment:
      - name: "OPENAI_API_KEY"
        from: "OPENAI_API_KEY"
```
Update application.yaml file as needed as per your selected number of agents. Above one is example of just 1 agent, you can add more as you want just rename the agent filename
that want to run and keep rest is same.

### Interface Agent

This agent allows Coral to send tasks to LangChain workflows.

### Requirements

Before moving on:
- Make sure you have an [OpenAI API key](https://platform.openai.com/account/api-keys)
- Python 3.10+ (use Anaconda)
- `uvicorn` installed (we'll use it to run the agent)

---

## Configure Agent Definitions

Now that you've selected your agents, it's time to configure them inside your `application.yaml` file.

This file tells Coral Server:
- Which agents to load
- How to start them
- What environment variables they need
- How to define applications and sessions


We'll edit the file we made earlier to have the agents we want.

Edit `config/application.yaml`

### Sample Config Structure

Here's a sample setup using 3 agents: `coral-interface`, `coral-repo`, and `coral-research`.

If you're following along, paste this into your `application.yaml` file.

```yaml
applications:
  - id: "app"
    name: "Default Application"
    description: "Default application for testing"
    privacyKeys:
      - "default-key"
      - "public"
      - "priv"

# Registry of agents we can orchestrate
registry:
  repounderstanding:
    # Exposed configuration for consumers of this agent
    options:
      - name: "OPENAI_API_KEY"
        type: "string"
        description: "OpenAI API Key"
      - name: "GITHUB_ACCESS_TOKEN"
        type: "string"
        description: "GitHub Access Token"

    # How this agent is actually orchestrated locally
    runtime:
      type: "docker"
      environment:
        - name: "API_KEY"
          from: "OPENAI_API_KEY"
        - name: "GITHUB_ACCESS_TOKEN"
          from: "GITHUB_ACCESS_TOKEN"
      image: "sd2879/coral-repounderstanding:latest"

  deepresearch:
    options:
      - name: "OPENAI_API_KEY"
        type: "string"
        description: "OpenAI API Key"
      - name: "LINKUP_API_KEY"
        type: "string"
        description: "LinkUp API Key. Get from https://linkup.so/"

    runtime:
      type: "docker"
      environment:
        - name: "API_KEY"
          from: "OPENAI_API_KEY"
      image: "sd2879/coral-opendeepresearch:latest"

  interface:
    options:
      - name: "OPENAI_API_KEY"
        type: "string"
        description: "OpenAI API Key"
      - name: "HUMAN_RESPONSE"
        type: "string"
        description: "Human response to be used in the interface agent"

    runtime:
      type: "docker"
      image: "sd2879/coral-interface-agent:latest"
      environment:
        - name: "API_KEY"
          from: "OPENAI_API_KEY"
        - name: "HUMAN_RESPONSE"
          from: "HUMAN_RESPONSE"

```

[//]: # (TODO: Explain the YAML structure and how to add more agents)
---

## Creating a Session
After editing your `application.yaml` file, the server will have hot-reloaded the changes, and you can now create a session to connect your agents.

1. Creating a session so agents can communicate

### What's Happening in This Step?

- The Coral server acts as a central hub.
- Sessions define which agents are active and how they talk.

### 1. Ensure the server has reloaded the new configuration

Check the coral server logs in the terminal where you started it. You should see messages indicating that the agents have been loaded successfully.
If it's running headless, you can check the logs by running:

```bash
docker logs coral-server
```

[//]: # (TODO: Link separately to different ways of creating sessions)
[//]: # (### Connect your Agents using a session)

[//]: # (#### Create a Session &#40;via Postman&#41;)

[//]: # (With the server running with the latest config, you now create a session to activate the agent.)

[//]: # ()
[//]: # (Endpoint)

[//]: # (```bash)

[//]: # (http://localhost:5555/sessions)

[//]: # (&#40;POST- Method&#41;)

[//]: # (```)

[//]: # ()
[//]: # (#### Instructions for Postman)

[//]: # ()
[//]: # (- Open Postman)

[//]: # (- Set method to POST)

[//]: # (- Use URL: http://localhost:5555/sessions)

[//]: # (- Under Body, select raw → JSON)

[//]: # (- Paste the JSON body shown below)

[//]: # (- Click Send)

[//]: # ()
[//]: # (JSON Body:)

[//]: # (```)

[//]: # ({)

[//]: # (  "sessionId": "test",)

[//]: # (  "applicationId": "app",)

[//]: # (  "privacyKey": "priv",)

[//]: # (  "agentGraph": {)

[//]: # (    "agents": {)

[//]: # (      "my-agent": {)

[//]: # (        "type": "local",)

[//]: # (        "agentType": "interface2",)

[//]: # (        "options": {)

[//]: # (          "OPENAI_API_KEY": "your-openai-key-here")

[//]: # (        })

[//]: # (      })

[//]: # (    },)

[//]: # (    "links": [["your agent name here"]])

[//]: # (  })

[//]: # (})

[//]: # (```)

[//]: # ()
[//]: # (### Expected Response)

[//]: # (```json)

[//]: # ({)

[//]: # (  "sessionId": "id here",)

[//]: # (  "applicationId": "value here",)

[//]: # (  "privacyKey": "value here")

[//]: # (})

[//]: # (```)
![Creating Session in UI](./assets/gifs/creating_session.gif)

### Creating a session via Coral Studio
In production, you would typically just make a POST request using your preferred HTTP client library from your application code.

For development purposes it makes sense to use Curl, Postman, or the Coral Studio UI to create sessions.

Let's use the Coral Studio UI to create a session.

### Sending Messages to Agents

You can also send prompts manually using the SendMessage API (for debugging or custom flows).

![Send Message API Flow](./assets/gifs/SendMesageAPi.gif)

> This is useful when testing agents without a UI or simulating user input.

---

## UI Exploration

We also explored the Coral debug UI. It currently focuses on session debugging, so we used Postman for input testing, which worked smoothly.

![Creating thread in coral-dbg](./assets/gifs/creating_thread.gif)

> The UI allows thread creation for active sessions, but interaction remains limited. Postman was used for input/output testing.
