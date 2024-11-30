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