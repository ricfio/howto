# Docker

## Docker Images Useful Commands

| command                                                                   | description                              |
|---------------------------------------------------------------------------|------------------------------------------|
| `docker image ls $PATTERN`                                                | Show all images matching $PATTERN        |

## Docker Containers Useful Commands

| command                                                                   | description                              |
|---------------------------------------------------------------------------|------------------------------------------|
| `docker container ls --all -f name=$PATTERN`                              | Show all containers matching $PATTERN    |
| `docker container ls --all -f ancestor=$IMAGE`                            | Show all containers built from '$IMAGE'  |
| `du -h $(docker inspect --format='{{.LogPath}}' $(docker ps -qa))`        | Show docker logs size for all containers |
| `cat /dev/null > $(docker inspect --format='{{.LogPath}}' $CONTAINER_ID)` | Clear log content for $CONTAINER_ID      |
| `docker cp [OPTIONS] $CONTAINER_NAME:$SRC_PATH $DEST_PATH`                | Copy files from container to localsystem |
| `docker cp [OPTIONS] $SRC_PATH $CONTAINER_NAME:$DEST_PATH`                | Copy files from localsystem to container |
| `docker exec -u 0 -it $CONTAINER_NAME bash`                               | Login into a container as root (bash)    |

## Appendix

### Docker Desktop on Windows (WSL2)

Setting boundaries for WSL2 (%USERPROFILE%/.wslconfig):

```ps
[wsl2]
memory=4GB # Limits VM memory in WSL 2 to 4 GB
processors=4 # Makes the WSL 2 VM use four virtual processors
```

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
