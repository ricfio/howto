# Linux

## Linux Useful Commands

| command                                              | description                                                  |
|------------------------------------------------------|--------------------------------------------------------------|
| `passwd`                                             | Change the user password                                     |
| `printenv `&#124;` grep <prefix>`                    | Print environment variables value with the prefix `<prefix>` |
| `wget -q -S -O - <url> 2>&1`                         | Print the response of a HTTP request at `<url>`              |
| `sudo update-alternatives --list php`                | List alternatives for PHP versions on Ubuntu                 |
| `sudo update-alternatives --set php /usr/bin/php8.1` | Set PHP versions on Ubuntu                                   |

## SSH Login without password

1. Generate SSH public and private keys on LOCAL_HOST

    ```bash
    ssh-keygen -t rsa
    ls ~/.ssh/
    ```

    ```console
    id_rsa  id_rsa.pub
    ```

2. Upload SSH public keys on REMOTE_HOST

    ```bash
    cat ~/.ssh/id_rsa.pub | ssh <remote_user>@<remote_host> 'mkdir -p ~/.ssh && chmod 700 ~/.ssh && cat >> ~/.ssh/authorized_keys && chmod 700 .ssh && chmod 640 .ssh/authorized_keys'
    ```

See also:

- [SSH](./ssh.md)

## [Process Informations](https://man7.org/linux/man-pages/man5/proc.5.html)

Save pidof variable for the process to monitor:

```bash
pidof=$(pidof mysqld)
```

Process Status Monitor:

```bash
while sleep 1; do clear; cat /proc/$pidof/status; done
```

You would like write all in a single command like:

```bash
while sleep 1; do clear; cat /proc/`pidof mysqld`/status; done
```

Other useful commands:

```bash
ls -lh /proc/$pidof/fd
less /proc/$pidof/smaps
ls -l /proc/$pidof/map_files | more
pmap $pidof -XX | less
```
