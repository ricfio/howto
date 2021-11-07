# Linux

## Linux Useful Commands

| command                           | description                                                 |
|-----------------------------------|-------------------------------------------------------------|
| `passwd`                          | Change the user password                                    |
| `printenv `&#124;` grep {PREFIX}` | Print environment variables value with the prefix {PREFIX}  |
| `wget -q -S -O - {URL} 2>&1`      | Print the response of a HTTP request                        |

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
    cat ~/.ssh/id_rsa.pub | ssh {REMOTE_USER}@{REMOTE_HOST} 'mkdir -p ~/.ssh && chmod 700 ~/.ssh && cat >> ~/.ssh/authorized_keys && chmod 700 .ssh && chmod 640 .ssh/authorized_keys'
    ```

See also:

- [SSH](./ssh.md)
