# Configure Agent Definitions

Now that you've selected your agents, it's time to configure them inside your `application.yaml` file.

This file tells Coral Server:
- Which agents to load
- How to start them
- What environment variables they need
- How to define applications and sessions

---

## Location of `application.yaml`

Place your config here inside the Coral Server repo:
```
coral-server/src/main/resources/application.yaml
```
---

## Sample Config Structure

Here’s a sample setup using 3 agents: `coral-interface`, `coral-repo`, and `coral-research`.

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
##  Define an Application (Required for Sessions)
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
