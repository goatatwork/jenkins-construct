# Jenkins

The included files facilitate quickly bringing up a Jenkins server via Docker Compose.

## Updating

There are better ways to update than just shutting down the docker compose project, updating the Dockerfile, building the container images, editing the docker-compose, and restarting. It would be cool if we implemented any of them. In the meantime:

Build like this (below) being cognizant of the version. The version we care about is in the FROM line in the Dockerfile.

```shell
docker build --file Dockerfile.jenkins -t myjenkins-blueocean:2.440.1 .
```

docker run --name jenkins-docker --rm --detach \
  --privileged --network jenkins --network-alias docker \
  --env DOCKER_TLS_CERTDIR=/certs \
  --volume jenkins-docker-certs:/certs/client \
  --volume jenkins-data:/var/jenkins_home \
  --publish 2376:2376 \
  docker:dind --storage-driver overlay2

