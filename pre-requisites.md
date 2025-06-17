# Prerequisites

Before you set up and run Coral, make sure your local environment has the following tools installed.

These are required to run agents, Coral Server, Coral Studio, and external LLMs like OpenAI.

---

## Required Tools & Versions

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

---

## Recommended Tools

| Tool | Reason |
|------|--------|
| **Anaconda** | Easy Python env management (optional but useful) |
| **Git Bash** (Windows) | Better than PowerShell for running shell commands |
| **Visual Studio Code** | IDE for editing agent code and config |
| **`.env` file support** | Use for storing API keys securely |

---

## Environment Variables You’ll Need

These are typically set in a `.env` file or passed into agents via `application.yaml`:

```env
OPENAI_API_KEY=sk-xxxxxxxxxxxxxxxxxxxxxx
GITHUB_PERSONAL_ACCESS_TOKEN=ghp-xxxxxxxxxxxx
LINKUP_API_KEY=linkup-xxxxxxxxxxxx
```
