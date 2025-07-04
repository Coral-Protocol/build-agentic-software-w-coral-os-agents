# Running Coral Server
In this guide we will get the coral server running locally.

## What is the Coral Server?
The Coral Server is a backend service that serves 2 purposes:
1. Allow agents to communicate with eachother via the Model Context Protocol (MCP)
2. Allows applications to create and manage agent graphs via the sessions API.

The server is written in Kotlin, but its APIs are language-agnostic, meaning you can use it with any programming language that supports HTTP requests and frameworks that support the Model Context Protocol (MCP).

## Getting the Coral Server running locally from source
This is the main recommended way of running the Coral server.
### Prerequisites
1. Git

### Steps
Clone the Coral repository:
```bash
git clone git@github.com:Coral-Protocol/coral-server.git
```

2) Change into the coral-server directory:
```bash
cd coral-server
```

3.Run from source
While the current directory is coral-server, run the following command to start the server:
```bash
./gradlew run
```
Note: Gradle is a build tool, that is here being used to run the Coral server. Gradle's built-in % progress bar won't go past 83%. This is normal.

When the serve is ready, you will see a message like this:
```
[DefaultDispatcher-worker-6] INFO io.ktor.server.Application - Responding at http://0.0.0.0:5555
```

If a JDK is not installed, ./gradlew should automatically download the JDK for you. If it does not, you can install a JDK manually. 
The Coral server requires at least JDK 17.

## Done
You now have the Coral server running locally. You can move on to the next guide.


## Troubleshooting
### Errors to ignore
There will be some errors and warnings that you can safely ignore, which will be listed here:
* 
### Address already in use
If you see an error like this:
```
java.net.BindException: Address already in use
```
This likely means that the server is already running in another terminal, or it was detached from a terminal and is still running in the background.

To resolve this, you can either:
1. Stop the currently running server by finding its process and killing it. You can do this with the following command:
   ```bash
   lsof -i :5555
   ```
   This will show you the process ID (PID) of the running server. You can then kill it with:
   ```bash
   kill -9 <PID>
   ```


