# Jenkins

The included files facilitate quickly bringing up a Jenkins server via Docker Compose.

## Updating

There are better ways to update than just shutting down the docker compose project, updating the Dockerfile, building the container images, editing the docker-compose, and restarting. It would be cool if we implemented any of them. In the meantime:

Build like this (below) being cognizant of the version. The version we care about is in the FROM line in the Dockerfile.

```shell
docker build --file Dockerfile.jenkins -t myjenkins-blueocean:2.440.1 .
```

```shell
docker compose up -d
```
