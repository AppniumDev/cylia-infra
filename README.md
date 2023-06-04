# Portainer Docker Drone Cylia infra setup
A Portainer + Caddy + Drone with automatic SSL setup for production using docker swarm.

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
9: Go to /portainer
    ```
    docker stack deploy -c docker-compose.yml portainer
    ```
10. Wait for services to go up
11. Navigate to https://portainer.cylia.cloud
12. Go to /drone