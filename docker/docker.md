# Docker

## Docker Useful Commands

| command                                                                   | description                              |
|---------------------------------------------------------------------------|------------------------------------------|
| `docker container ls --all -f ancestor=$IMAGE`                            | Show all containers built from '$IMAGE'  |
| `du -h $(docker inspect --format='{{.LogPath}}' $(docker ps -qa))`        | Show docker logs size for all containers |
| `cat /dev/null > $(docker inspect --format='{{.LogPath}}' $CONTAINER_ID)` | Clear log content for $CONTAINER_ID      |
| `docker cp [OPTIONS] $CONTAINER_NAME:$SRC_PATH $DEST_PATH`                | Copy files from container to localsystem |
| `docker cp [OPTIONS] $SRC_PATH $CONTAINER_NAME:$DEST_PATH`                | Copy files from localsystem to container |

References:

- [https://stackoverflow.com/questions/59765204/how-to-list-docker-logs-size-for-all-containers]
- [https://access.redhat.com/solutions/2334181]
- [https://docs.docker.com/engine/reference/commandline/cp/]

## Appendix

## Container filters

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
