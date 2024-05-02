## Using ngrok with Docker Compose

If you're more comfortable using Docker Compose, you can use the following as a starting point. Copy the contents below into a new file named docker-compose.yaml, then run docker compose up in that directory. This Docker compose file assumes that you have an ngrok.yml file in the same directory with at least one tunnel defined. Check out the [ngrok agent config file documentation](https://ngrok.com/docs/agent/config/#full-example) for help creating a configuration file with a tunnel definition. If you want to use the same configuration file as your local ngrok agent, you can view the location of the default config file using ngrok config check.

```
services:
    ngrok:
        image: ngrok/ngrok:latest
        restart: unless-stopped
        command:
          - "start"
          - "--all"
          - "--config"
          - "/etc/ngrok.yml"
        volumes:
          - ./ngrok.yml:/etc/ngrok.yml
        ports:
          - 4040:4040
```