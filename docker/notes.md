# Docker Notes

- [Devops With Docker Helinski MOOC](https://courses.mooc.fi/org/uh-cs/courses/devops-with-docker)

## CH2

## Basics
Most used commands:
- `docker image ls`: lists all images
- `docker image rm <image>`: removes an image
- `docker image pull <image>`: download image without running it
- `docker container ls -a`: list all running _and_ stopped containers
- `docker container run <image>`: runs container from image
- `docker container rm <container>`: removes a container
- `docker container stop <container>`: stops a container
- `docker container exec <container>`: executes a command inside the container
  - Ex, open interactive bash shell in container: `docker container exec -it <container> bash`

<details><summary>How to filter list of containers?</summary>

- `docker container ls -a | grep <name>`
</details>

<details><summary>What are "dangling images"?</summary>

- images that don't have a name and are not used
- usually automatically generated during build
</details>

<details><summary>How to remove all stopped containers and dangling images?</summary>

- `docker container prune`
- `docker image prune`
</details>

<details><summary>Can you remove a running container?</summary>

- No, need to first stop the container
- `docker container stop <name>`
- or `docker container rm --force <name>`
</details>

<details><summary>What does the `i` in `docker run -it <image>` do?</summary>

- Allows you to interact with the container 
</details>

<details><summary>How do you display existing and new logs from container?</summary>

- `docker logs -f <container>`
- `docker attach <container>`
  - this option allows you to also interact with the container
</details>

<details><summary>What's the difference between `docker stop` and `docker kill`</summary>

- `docker stop` sends SIGTERM followed by SIGKILL after 10 seconds
- `docker kill` sends SIGKILL right away to force termination
  - `docker rm --force <container>` is `docker kill` followed by `docker rm`
</details>

<details><summary>How to run a container so that it automatically removes itself after it exits</summary>

- `docker run --rm`
</details>

<details><summary>How do you exit out of an attached container?</summary>

- `CTRL-P` then `CTRL-Q`
</details>

<details><summary>Where do docker images come from?</summary>

- When running command like `docker run <image>`, Docker will first search local and then search Docker Hub for the image of the same name
</details>

<details><summary>How to search for images?</summary>

- `docker search <image>`
</details>

<details><summary>What are "tags"?</summary>

- Refers to specific versions of an image
- Allows you to rename specific images
</details>

<details><summary>How would you tag a Docker image for convenience?</summary>

- Ex: `docker tag ubuntu:25.04 ubuntu:latest_lts`
</details>

<details><summary>Exercise 1.5</summary>

- `docker image pull devopsdockeruh/simple-web-service:ubuntu`
- `docker image pull devopsdockeruh/simple-web-service:alpine`
- `docker image ls` (to see sizes)
- `docker run -d --rm -it devopsdockeruh/simple-web-service:alpine`
- `docker exec -it <alpine-container> sh` (bash does not work on alpine)
- `tail -f ./text.log`
</details>

<details><summary>Exercise 1.6</summary>

- `docker run -it devopsdockeruh/pull_exercise`
- Navigate to "https://hub.docker.com/r/devopsdockeruh/pull_exercise" for password
</details>

<details><summary>What is a Dockerfile</summary>

- file that contains build instructions for an image
- Ex:
```
# Start from the alpine image that is smaller but no fancy tools
FROM alpine:3.21

# Use /usr/src/app as our workdir. The following instructions will be executed in this location.
WORKDIR /usr/src/app

# Copy the hello.sh file from this directory to /usr/src/app/ creating /usr/src/app/hello.sh
COPY hello.sh .

# Alternatively, if we skipped chmod earlier, we can add execution permissions during the build.
# RUN chmod +x hello.sh

# When running "docker run", the command will be "./hello.sh"
CMD ["./hello.sh"]

### hello.sh
# #!/bin/sh
# echo "Hello, docker!"
###
```
</details>

<details><summary>How would you build a dockerfile?</summary>

- `docker build -t <image-name> <file location>`
- `docker build` will result in an image being created
</details>

<details><summary>What are layers and how do they result in faster builds?</summary>

- Each instruction in Dockerfile translates to a layer in the final image
- Whenever layer changes, only that layer and subsequent layers after it will need to be re-built
  - That's why dockerfiles should have layers ordered from least-frequently changed to most-frequently changed
- Other layers can be sourced from the cache and will not need to be re-run
- Layer caching results in signficant reduction in build times
- [See docs](https://docs.docker.com/build/cache/)
</details>

<details><summary>What instruction in Dockerfile is not executed during build time?</summary>

- `CMD [...]`, its only run during `docker run ...`
</details>

<details><summary>How to save changes in a container as a new image?</summary>

- Container way:
  - Run container and make changes (save, modify, remove, etc files in the container)
  - Check what changed: `docker diff <container_name>`
  - Save as new image: `docker commit <container_name> <image name>`
- Dockerfile way:
  - simply modify the dockerfile and build it as a new image (by renmaing it or adding a tag)
</details>

<details><summary>Exercise 1.7</summary>

- [source](https://courses.mooc.fi/org/uh-cs/courses/devops-with-docker/chapter-2/in-depth-dive-into-images)
- Dockerfile
```yaml
FROM ubuntu:24.04

WORKDIR /usr/src/app

RUN apt-get update && apt-get install -y curl

COPY script.sh .

RUN chmod +x script.sh

CMD ["./script.sh"]
```
- Build command: `docker build -t curler .`
- Run command: `docker run -it curler`
</details>

<details><summary>Exercise 1.8</summary>

- Dockerfile:

```yaml
FROM devopsdockeruh/simple-web-service:alpine

CMD ["server"]
```

- Build command: `docker build -t web-server .`
- Run command: `docker run web-server`
</details>

<details><summary></summary>
</details>