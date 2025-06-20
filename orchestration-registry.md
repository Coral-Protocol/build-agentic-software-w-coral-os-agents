## Example registry
```yaml
registry:
  test:  
    options:
      - name: "NAME"
        type: "string"
        description: "Test agent name"
      - name: "API_KEY"
        type: "string"
        description: "Some API key the agent needs"
      - name: "API_TIMEOUT"
        type: "number"
        default: 10000
description: "Connection timeout to the API"
    runtime:  
      type: "executable"  
      command: ["python", "-u", "my-agent.py"]  
      environment:
        - option: "NAME" # pass the 'NAME' option in as an env var
        - name: "SPECIFIC_API_KEY" # pass the 'API_KEY' as an env var called 'SPECIFIC_API_KEY'
          from: "API_KEY"
        - option: "API_TIMEOUT"
        - name: "DEBUG_MODE" # pass in an env var called "DEBUG_MODE",
  value: "ENABLE"    # with the value "ENABLE"
```

## Specification
- `registry` is a map of an agent type (unique name for this kind of agent), to an agent definition

An agent definition is comprised of:
- `options`, a list of configuration options we want to expose to users of this kind of agent
- each option has the following fields:
- `name` - the name of the option
- `type` - `"string"` or `"number"` (more to be added)
- `description` - human readable description for this option
- `default` - an optional default value for this option
- if `default` is not set, the option is required to be set when orchestrated
- `runtime` lets you define how the agent is actually orchestrated when requested
- `type` determines what kind of runtime (docker, k8s, etc)
- currently only `"executable"` is supported, which runs a command as a sub-process, and has the following associated fields:
- `command` - list of arguments composing the final command
- it's best practice to put each part of a command as individual items in the list, since different shells can handle argument separation differently
- `environment` - list of environment variables to set when running the command
- each environment variable can take *any* of the following forms:
1. `name`/`value` - a static environment variable where `name`=`value`
2. `name`/`from` - an environment variable where the value is derived from an option, where `from` is the option we pull the value from
3. `option` - shorthand for `name`/`from`, for when they both have the same value

## Coral connection url
- When using orchestration, an extra environment variable (`CORAL_CONNECTION_URL`) is automatically injected, to provide the agent with the correct SSE url for connecting to Coral. This is the same with executable runtime and the docker runtime.
