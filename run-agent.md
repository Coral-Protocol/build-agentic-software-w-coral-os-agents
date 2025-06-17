# Run the Agent

Now that the Coral server is running and a session has been created, it’s time to run your Agent so it can listen for and respond to messages.

---

## Running the agent means:
- Coral can trigger it based on the session
- It will handle user messages or call external tools (like OpenAI)

---

# Run Agents
## Navigate to the Agent Directory

Now that your Coral Server is running and your session is created, it’s time to run your selected agents locally.
Each agent runs independently and connects back to Coral Server to participate in a live session.

This guide shows how to run one or multiple agents side-by-side.

---

## 1. Confirm Agents in `application.yaml`

Open your Coral Server config:
```
coral-server/src/main/resources/application.yaml
```
And in this file you registered all your agents that you want (we explained this in the previous file)

## 2. Clone Agent Repos (if needed)
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
## 3. Run Agents (One Per Terminal)
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

## Final Running files?

| Terminal         | Task                                     |
|------------------|------------------------------------------|
| Terminal 1       | Coral Server (`./gradlew run`)           |
| Terminal 2       | Interface Agent (`uv run 0-langchain-interface.py`) |
| Postman / curl   | Session creation request (`/sessions`)   |

