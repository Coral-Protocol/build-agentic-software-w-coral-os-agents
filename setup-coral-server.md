# Set Up Coral Server (Backend)

**Coral Server** is the engine that runs your multi-agent sessions, executes agent logic, and facilitates communication between agents.

In this step, you’ll set up and start Coral Server locally using your own `application.yaml` config.

---

## 1. Clone the Coral Server Repository

Navigate to your project root and run:

```bash
git clone https://github.com/Coral-Protocol/coral-server.git
```

## 2. Move into the server directory
bash
```
cd coral-server
```
## 3. Install dependencies
If you’re using npm:
bash
```
npm install
```
Or use pnpm install if your system is configured to use pnpm.

## 4. Ensure You Have an application.yaml
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

## What's Next?

Now that Coral Server is up, your next step is to:
- Choose your agents
- Add them to your application.yaml
- Prepare for session creation
