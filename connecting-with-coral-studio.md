# Coral Studio
Coral Studio is a web-based tool for interacting with the Coral server, and observing the connected agents and their interactions.

It also allows you to create a session with agents through the interface, which constructs a POST to the sessions api, which you can copy from your network tab in your browser's developer tools to use in your own application.


## Running Coral Studio

Run the following command to start Coral Studio:
```
npx @coral-protocol/coral-studio
```

This will start a local server that serves the Coral Studio interface.

## Connecting to the Coral Server
When you open Coral Studio in your browser, it will prompt you to enter the URL of the Coral server you want to connect to. Enter the URL of your Coral server (e.g., `http://0.0.0.0:5555` if you're running it locally).

[Note!] Some ad-blockers require that you connect to the server via a host address matching the URL in the address bar, so if you run the Coral server on 0.0.0.0, you need to connect to it via `0.0.0.0:5555`, not `localhost:5555`, unless you're connected to coral studio via `localhost:5555` as well.

## Using Coral Studio

See https://github.com/Coral-Protocol/coral-studio/