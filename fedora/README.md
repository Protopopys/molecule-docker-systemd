# Fedora latest stable image with systemd enabled

You can use this image as a base container to run systemd services inside.

## Supported tags
 - `latest`

## Usage

Run the container as a daemon

`docker run -d --name systemd-fedora --privileged -v /sys/fs/cgroup:/sys/fs/cgroup:ro protopopys/systemd-fedora`

Enter to the container

`docker exec -it systemd-fedora bash`

Remove the container

`docker rm -f systemd-fedora`
