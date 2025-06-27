
## Running Coral Protocol Agents with Docker
It makes the most sense to run only the agents in docker, since the server itself and coral studio do not have native dependencies that require docker.

If you're really struggling to run the coral server locally, you can run it in docker as well, but it's not recommended:



### Pull the Agent Docker Images

```bash
docker pull coralprotocol/coral-repounderstanding
docker pull coralprotocol/coral-opendeepresearch
docker pull coralprotocol/coral-interface-agent
```


### Troubleshooting

## Server logs in docker
If it's running in docker, you can check the logs by running:
```bash
docker logs coral-server
```
