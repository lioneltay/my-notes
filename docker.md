# Docker Notes

- `docker container rm $(docker contain ls -a -q)`
  - Delete all containers

- `docker run -it <image-name>`
  - Run docker container with terminal

- `docker run <image-name> <command>`
  - Runs a image but override the command with `<command>`

- `docker container run` is short for `docker create` and `docker start` (with minor differences)
  - `docker container run` attaches to STDOUT so you can see messages
  - `docker container create` -> `docker container start` does not attaches to STDOUT so you can see messages

- `docker system prune`
  - This will remove:
    - all stopped containers
    - all networks not used by at least one container
    - all dangling images
    - all dangling build cache

- `docker container logs <container-id>`
  - show the logs of the container

- `docker container stop <container-id>`
  - Stops the container by sending SIGTERM giving the container time to stop
  - If the container does not stop itself after 10 seconds it sends a KILLSIG to stop it immediately

- `docker container kill <container-id>`
  - Send a KILLSIG to the container right away

- `docker exec -it <container-id> <command>`
  - `-i` allows your input to be piped into the containers STDIN
  - `-t` allows the output of the container to be nicely formatted in your terminal
  - Run a command in an existing container


## Dockerfile

- `FROM`
  - Set the base image to build your image upon
- `WORKDIR`
  - Set the current working directory when in the container
- `COPY`
  - Copy files from the build directory into the container
- `RUN`
  - Run a command in the container
- `CMD`
  - Set the start command of the image

## docker-compose

- docker-compose automatically creates the service containers within the same network

- `docker-compose up --build`
  - Run the containers, building the containers first if anything has changed

- `docker-compose down`
  - Stop and clean up the containers
  - Stop and remove containers, networks, images, and volumes

- config
  - version: "3"
  - services:
    - <servicename>:
      - image: Existing image
      - build: build the image from a dockerfile config
      - ports: list of port mappings
      - restart:
        - "no": never restart
        - always: always restart
        - on-failure: restart on failure
        - unless-stopped: restart unless manually stopped