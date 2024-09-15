# Docker

- [Docker CLI Cheat Sheet](https://docs.docker.com/get-started/docker_cheatsheet.pdf)

## Docker Image

| command                                  | description                              |
|------------------------------------------|------------------------------------------|
| `docker image ls --all`                  | Show all images (includes intermediates) |
| `docker image ls --all $PATTERN`         | Show all images matching $PATTERN        |
| `docker image ls --all -f dangling=true` | Show dangling images                     |
| `docker image prune -f`                  | Prune dangling images                    |

## Docker Container

| command                                                    | description                              |
|------------------------------------------------------------|------------------------------------------|
| `docker container ls --all`                                | Show all containers                      |
| `docker container ls --all -f name=$PATTERN`               | Show all containers matching $PATTERN    |
| `docker container ls --all -f ancestor=$IMAGE`             | Show all containers built from '$IMAGE'  |
| `docker cp [OPTIONS] $CONTAINER_NAME:$SRC_PATH $DEST_PATH` | Copy files from container to localsystem |
| `docker cp [OPTIONS] $SRC_PATH $CONTAINER_NAME:$DEST_PATH` | Copy files from localsystem to container |
| `docker exec -u 0 -it $CONTAINER_NAME bash`                | Login into a container as root (bash)    |

### Docker Container Log

| command                                                                 | description                              |
|-------------------------------------------------------------------------|------------------------------------------|
| `docker logs -f <container>`                                            | Show logs of container                   |
| `sudo du -h $(docker inspect --format='{{.LogPath}}' $(docker ps -qa))` | Show docker logs size for all containers |
| `cat /dev/null > $(docker inspect --format='{{.LogPath}}' <container>)` | Clear log content for container          |

## Appendix

### Container filters

`docker container ls --all --filter=...`

```console
Filter output based on these conditions:
- ancestor=(<image-name>[:tag]|<image-id>| ⟨image@digest⟩)
  containers created from an image or a descendant.
- before=(<container-name>|<container-id>)
- expose=(<port>[/<proto>]|<startport-endport>/[<proto>])
- exited=<int> an exit code of <int>
- health=(starting|healthy|unhealthy|none)
- id=<ID> a container's ID
- isolation=(default|process|hyperv) (Windows daemon only)
- is-task=(true|false)
- label=<key> or label=<key>=<value>
- name=<string> a container's name
- network=(<network-id>|<network-name>)
- publish=(<port>[/<proto>]|<startport-endport>/[<proto>])
- since=(<container-name>|<container-id>)
- status=(created|restarting|removing|running|paused|exited)
- volume=(<volume name>|<mount point destination>)
```

## References

- [Change Docker root directory /var/lib/docker to another location](https://linuxconfig.org/how-to-move-docker-s-default-var-lib-docker-to-another-directory-on-ubuntu-debian-linux)
- [List docker logs size for all containers](https://stackoverflow.com/questions/59765204/how-to-list-docker-logs-size-for-all-containers)
- [Set container log limits](https://access.redhat.com/solutions/2334181)
- [Copy files/folders between a container and the local filesystem](https://docs.docker.com/engine/reference/commandline/cp/)
