
# Adding and using Custom Agents to your Multi-agent application

## Adding your own agent is very simple
Since in the main tutorial we're running the agents from source code anyway, you could simply go and edit one of them.

For clarity though here are all of the steps that are needed for adding a custom agent.

### Summary
1. Create your agent code, putting it in a file with a known location relative to the Coral server's working directory.


## Adding an agent that runs from source in your application.yml agent registry
To add your own agent, edit the application.yml file in src/main/resources and add your agent to the agents section. For example, if you have an agent called "my-custom-agent", you would add it like this:

```yaml
  coral-research:
    options:
      - name: "OPENAI_API_KEY"
        type: "string"
        description: "OpenAI API Key for OpenDeepResearch agent"
      - name: "LINKUP_API_KEY"
        type: "string"
        description: "LinkUp API Key for OpenDeepResearch agent"
    runtime:
      type: "executable"
      command:
              [
                "bash",
                "-c",
                "python ../custom-agent.py",
              ]
      environment:
        - name: "OPENAI_API_KEY"
          from: "OPENAI_API_KEY"
        - name: "LINKUP_API_KEY"
          from: "LINKUP_API_KEY"
```