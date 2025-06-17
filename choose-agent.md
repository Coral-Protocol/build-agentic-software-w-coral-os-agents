# Choose Your Agent

Before building a multi-agent system, we need to decide **what kind of task our agent will perform**. With **Coral**, you can pick from a list of existing agents OR write your own.

Coral supports a modular approach using agents and in our case, we are using an **Interface Agent**, which wraps powerful tools like LangChain, OpenAI.

---

## What is Agent?

An agent is simply:
- A Python (or other) script
- That follows a communication protocol
- And can be called by Coral to perform tasks

---

## Choose Agents from Coral Awsome Agents

Visit the official Coral community list:

- [Awsome Agents for Multi-agent systems](https://github.com/Coral-Protocol/awesome-agents-for-multi-agent-systems)

  <img width="467" alt="Image" src="https://github.com/user-attachments/assets/07fc07cf-8f32-407c-9252-cca6277d4043" />

From there, pick one. For this tutorial, we’re using:

## Choose Agents for Your Use Case

Pick 1–3 agents depending on your goal.

Example setup:

| Agent ID | Description |
|----------|-------------|
| `coral-interface` | An interface agent that coordinates actions |
| `coral-research` | Performs deep research using LLM + tools |
| `coral-repo` | Analyzes GitHub repos using LangChain |

You can mix & match based on what you’re trying to build.

---

## Copy Agent Snippets (YAML Format)

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

---

## Requirements

Before moving on:
- Make sure you have an [OpenAI API key](https://platform.openai.com/account/api-keys)
- Python 3.10+ (use Anaconda)
- `uvicorn` installed (we’ll use it to run the agent)
