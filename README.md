# Portainer Docker Cylia infra setup
A Portainer + Caddy with automatic SSL setup for production using docker swarm.

## Steps
1. Access VPS via SSH
2. Navigate to /opt/
3. Clone this repository
4. Install Docker if not already present
5. Init Docker Swarm
6. Create two external Docker Swarm networks
    ```
    docker network create -d overlay --attachable agent_network
    docker network create -d overlay --attachable caddy_public
    ```
7. Go to /caddy
    ```
    docker stack deploy -c docker-compose.yml caddy
    ```
8. Wait for service to go up
    If replicas 0/1 --> "docker compose up" and repeat from step 7, add missing folders inside caddy folder (caddy_config, caddy_data)
    ```
    cd caddy
    mkdir caddy_config
    mkdir caddy_data
    ```

9: Go to /portainer
    ```
    docker stack deploy -c docker-compose.yml portainer
    ```
10. Wait for services to go up
11. Navigate to https://portainer.cylia.io 
    (license code: 2-pOmAbAsu5X470fbohGA/ydBvNjHH3fyto1XeSY1kJCe9vb0LHkZBUdDp/8b2lsemdT0dZOeOK8c4EyK7mGOAA==)

    (license code: 2-KhbQe2lwPE+97hQW2eQPHxfxjCBgP+blt5o7cUFV4zD+QtghmPhTq4zCur04bT+EglDtzWZMHRn7SYvi9ZVn)


## Caddy file reload
    ```
    docker exec -w /etc/caddy ${docker_container_id} caddy reload
    ```