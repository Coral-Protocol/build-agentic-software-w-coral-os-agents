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
npx @coralprotocol/coral-studio@latest
```

This will start the Studio UI at:
```
http://localhost:3000
```
Your browser should open automatically. If it doesn't, open it manually.

### 2. Confirm It's Working
You should see:
- A homepage for Coral Studio
- An option to create a session or connect to Coral Server
- A visual interface to select agents and manage interactions

Coral-UI should look like this
<img width="957" alt="Image" src="https://github.com/user-attachments/assets/819ce48e-b740-459f-a0aa-9eb23ec66c1f" />

---

## Run the coral server

**Coral Server** is the engine that runs your multi-agent sessions, executes agent logic, and facilitates communication between agents.

In this step, you'll set up and start Coral Server locally using your own `application.yaml` config.

### 1. Clone the Coral Server Repository

Navigate to your project root and run:

```bash
git clone https://github.com/Coral-Protocol/coral-server.git
```

### 2. Move into the server directory
```bash
cd coral-server
```
### 3. Run the Coral Server with Gradle
To start the Coral Server, run:

```bash
./gradlew run
```

This will launch the server,
which acts as a control pane that creates instances of agents
connected to their individualised MCP servers allowing them to communicate and collaborate.

### 4. Ensure You Have an application.yaml
Your configuration file should be placed here:
```
coral-server/src/main/resources/application.yaml
```
It defines:
- Agents to load
- Runtime commands
- Application sessions

Sample structure (application.yaml):
```
registry:
  coral-interface:
    runtime:
      command: ["bash", "-c", "cd ../Coral-Interface-Agent && uv sync && uv run python 0-langchain-interface.py"]
      environment:
        - name: OPENAI_API_KEY
          from: OPENAI_API_KEY

applications:
  - id: "app"
    name: "Multi-Agent Test App"
    privacyKeys:
      - "priv"
```

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

### Location of `application.yaml`

Place your config here inside the Coral Server repo:
```
coral-server/src/main/resources/application.yaml
```

### Sample Config Structure

Here's a sample setup using 3 agents: `coral-interface`, `coral-repo`, and `coral-research`.

```yaml
registry:
  coral-interface:
    options:
      - name: "OPENAI_API_KEY"
        type: "string"
        description: "OpenAI API Key for Interface Agent"
    runtime:
      type: "executable"
      command:
        [
          "bash",
          "-c",
          "cd ../Coral-Interface-Agent && uv sync && uv run <name of your agent file in .py format>"
        ]
      environment:
        - name: "OPENAI_API_KEY"
          from: "OPENAI_API_KEY"

  coral-repo:
    options:
      - name: "OPENAI_API_KEY"
        type: "string"
      - name: "GITHUB_PERSONAL_ACCESS_TOKEN"
        type: "string"
    runtime:
      type: "executable"
      command:
        [
          "bash",
          "-c",
          "cd ../Coral-RepoUnderstanding-Agent && uv sync && uv run <name of your agent file in .py format>"
        ]
      environment:
        - name: "OPENAI_API_KEY"
          from: "OPENAI_API_KEY"
        - name: "GITHUB_PERSONAL_ACCESS_TOKEN"
          from: "GITHUB_PERSONAL_ACCESS_TOKEN"

  coral-research:
    options:
      - name: "OPENAI_API_KEY"
        type: "string"
      - name: "LINKUP_API_KEY"
        type: "string"
    runtime:
      type: "executable"
      command:
        [
          "bash",
          "-c",
          "cd ../Coral-OpenDeepResearch-Agent && uv sync && uv run python <name of your agent file in .py format>"
        ]
      environment:
        - name: "OPENAI_API_KEY"
          from: "OPENAI_API_KEY"
        - name: "LINKUP_API_KEY"
          from: "LINKUP_API_KEY"
```

###  Define an Application (Required for Sessions)
At the bottom of the file, define your app like this:
```
applications:
  - id: "app"
    name: "any name"
    description: "any description"
    privacyKeys:
      - "priv"
```
This applicationId and privacyKey are required when creating sessions via Coral Studio or Postman.

---

## Start Coral Server & Create a Session

This step covers two key actions:
1. Starting the Coral backend
2. Creating a session so agents can communicate

### What's Happening in This Step?

- The Coral server acts as a central hub.
- Sessions define which agents are active and how they talk.
- You'll start the server using Gradle, then create a session using Postman.

### 1. Start the Coral Server

Open a new terminal window and navigate to your `coral-server` folder.
Run by using following command.

```bash
cd coral-server
./gradlew run
```
This starts the server on:
```
http://localhost:5555
```
| Note: Gradle may appear and stop at 83%, but the server is running. Check the terminal logs to confirm. Leave this terminal running! The server must stay active while testing.

### Connect your Agent using a session

#### Create a Session (via Postman)
With the server running, you now create a session to activate the agent.

Endpoint
```bash
http://localhost:5555/sessions
(POST- Method)
```

#### Instructions for Postman

- Open Postman
- Set method to POST
- Use URL: http://localhost:5555/sessions
- Under Body, select raw → JSON
- Paste the JSON body shown below
- Click Send

JSON Body:
```
{
  "sessionId": "test",
  "applicationId": "app",
  "privacyKey": "priv",
  "agentGraph": {
    "agents": {
      "my-agent": {
        "type": "local",
        "agentType": "interface2",
        "options": {
          "OPENAI_API_KEY": "your-openai-key-here"
        }
      }
    },
    "links": [["your agent name here"]]
  }
}
```

### Expected Response
```json
{
  "sessionId": "id here",
  "applicationId": "value here",
  "privacyKey": "value here"
}
```
![Creating Session in UI](./assets/gifs/creating_session.gif)

### Sending Messages to Agents

You can also send prompts manually using the SendMessage API (for debugging or custom flows).

![Send Message API Flow](./assets/gifs/SendMesageAPi.gif)

> This is useful when testing agents without a UI or simulating user input.

---

## Run the Agent

Now that the Coral server is running and a session has been created, it's time to run your Agent so it can listen for and respond to messages.

### Running the agent means:
- Coral can trigger it based on the session
- It will handle user messages or call external tools (like OpenAI)

### Run Agents
#### Navigate to the Agent Directory

Now that your Coral Server is running and your session is created, it's time to run your selected agents locally.
Each agent runs independently and connects back to Coral Server to participate in a live session.

This guide shows how to run one or multiple agents side-by-side.

### 1. Confirm Agents in `application.yaml`

Open your Coral Server config:
```
coral-server/src/main/resources/application.yaml
```
And in this file you registered all your agents that you want (we explained this in the previous file)

### 2. Clone Agent Repos (if needed)
Make sure all agent directories are cloned as siblings of your Coral Server folder:
```
your-root/
├── coral-server/
├── Coral-Interface-Agent/
├── Coral-RepoUnderstanding-Agent/
├── Coral-OpenDeepResearch-Agent/
```
Clone using:
```
git clone https://github.com/Coral-Protocol/Coral-Interface-Agent.git
git clone https://github.com/Coral-Protocol/Coral-RepoUnderstanding-Agent.git
git clone https://github.com/Coral-Protocol/Coral-OpenDeepResearch-Agent.git
```

### 3. Run Agents (One Per Terminal)
You must run each agent in its own terminal.

Terminal 1:
```
cd Coral-Interface-Agent
uv run python <name of your agent file>
```

Terminal 2:
```
cd Coral-RepoUnderstanding-Agent
uv run python <name of your agent file>
```

Terminal 3:
```
cd Coral-OpenDeepResearch-Agent
uv run python <name of your agent file>
```

If everything is set up correctly, your terminal should output something like (example of 1 agent below):
```
Agent: How can I assist you today?
```
![Image](https://github.com/user-attachments/assets/8ae26013-ad64-4d98-a93c-100e733cf6a2)

This confirms the agent is running and connected to the Coral session.

![Agent Running in Terminal](./assets/gifs/AgentTerminalRunning.gif)

### Final Running files?

| Terminal         | Task                                     |
|------------------|------------------------------------------|
| Terminal 1       | Coral Server (`./gradlew run`)           |
| Terminal 2       | Interface Agent (`uv run 0-langchain-interface.py`) |
| Postman / curl   | Session creation request (`/sessions`)   |

---

## UI Exploration

We also explored the Coral debug UI. It currently focuses on session debugging, so we used Postman for input testing, which worked smoothly.

![Creating thread in coral-dbg](./assets/gifs/creating_thread.gif)

> The UI allows thread creation for active sessions, but interaction remains limited. Postman was used for input/output testing.
