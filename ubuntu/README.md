# Ubuntu image with systemd enabled

You can use this image as a base container to run systemd services inside.

## Supported tags
 - `20.04`, `latest`
 - `18.04`
 - `16.04`

## Usage

Run the container as a daemon

`docker run -d --name systemd-ubuntu --security-opt seccomp=unconfined --tmpfs /run --tmpfs /run/lock -v /sys/fs/cgroup:/sys/fs/cgroup:ro protopopys/systemd-ubuntu:$TAG`

Enter to the container

`docker exec -it systemd-ubuntu bash`

Remove the container

`docker rm -f systemd-ubuntu`

For Ansible Molecule

```yaml
platforms:
  - name: Ubuntu$TAG
    hostname: ubuntu_$TAG
    image: protopopys/systemd-ubuntu:$TAG
    override_command: False
    tty: True
    privileged: True
    security_opts:
      - seccomp=unconfigured
    volumes:
      - "/sys/fs/cgroup:/sys/fs/cgroup:ro"
    tmpfs:
      - /tmp
      - /run/lock
```