# Docker Notes

- [Devops With Docker Helinski MOOC](https://courses.mooc.fi/org/uh-cs/courses/devops-with-docker)

## CH2

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