# Step 6: Start Coral Server & Create a Session

This step covers two key actions:
1. Starting the Coral backend
2. Creating a session so agents can communicate

---

## What’s Happening in This Step?

- The Coral server acts as a central hub.
- Sessions define which agents are active and how they talk.
- You’ll start the server using Gradle, then create a session using Postman.

---

## 1. Start the Coral Server

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

## Connect your Agent using a session

### Create a Session (via Postman)
With the server running, you now create a session to activate the agent.

Endpoint
bash
```
http://localhost:5555/sessions
(POST- Method)
```

# Instructions for Postman

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

## Expected Response
json
```
{
  "sessionId": "id here",
  "applicationId": "value here",
  "privacyKey": "value here"
}
```
![Creating Session in UI](./assets/gifs/creating_session.gif)

# Sending Messages to Agents

You can also send prompts manually using the SendMessage API (for debugging or custom flows).

![Send Message API Flow](./assets/gifs/SendMesageAPi.gif)

> This is useful when testing agents without a UI or simulating user input.
