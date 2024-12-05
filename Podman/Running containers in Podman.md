To run a container in Podman, use the following command:
`podman run -dt <image>`
Here, you can specify the image name by doing a `podman search` then copying over the image name that shows up.
The command above just did the following:
* `podman run` runs a container. If nothing is specified, this creates a new container.
* `-d or --detach` using this option makes it so the container is ran in the background.
* `-t or --tty` allocates a pseudo-TTY. Runs a throwaway container shell.
# Running Podman as root
You can run `podman` images as root as well. For example:
`sudo podman run -dt --name rootubi8 registry.access.redhat.com/ubi8` does the following:
* `-d` makes the container run in detached mode
* `-t` allocates a `tty` for that container
* `--name` specifies a name for the container
Pausing and unpausing containers can only be done using `root` for now.

# Working with running containers
You can generally execute a command within a container using the following as a guide:
`podman exec <container_name> <command>`
To enter a running container's shell you can use the following command as an example:
`podman exec -it mynginx /bin/bash`
This command does the following:
* `-i or --interactive` makes an interactive process
* `-t or --tty` allocates a pseudo-tty.

---
#container #podman #linux 