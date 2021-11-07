# SSH

## SSH Login without password

User 'rik' wants to SSH login without password from him host 'ssh-client' to the host 'ssh-server' as user 'bob':  

```
[rik@ssh-client ~]# # User rik at Host SSH Client
[bob@ssh-server ~]# # User bob at Host SSH Server
```

# Host SSH Client

1. rik@ssh-client: Generate public/private rsa keys

    `ssh-keygen -t rsa`

    ```
    Generating public/private rsa key pair.
    Enter file in which to save the key (/root/.ssh/id_rsa):
    Created directory '/root/.ssh'.
    Enter passphrase (empty for no passphrase):
    Enter same passphrase again:
    Your identification has been saved in /root/.ssh/id_rsa.
    Your public key has been saved in /root/.ssh/id_rsa.pub.
    The key fingerprint is:
    SHA256:UEbeAVbkbcScIa/jGjv09R1QuYXcKY8zUaMs2VWscSk root@ssh-client
    The key's randomart image is:
    +---[RSA 2048]----+
    |       .*+=oo+.B*|
    |       = o *BE*=*|
    |      . . oo++B+o|
    |       .   o.=.o |
    |        S o   +  |
    |        .. ..  . |
    |       ..... . ..|
    |        .+.   . .|
    |        o.       |
    +----[SHA256]-----+
    ```

2. rik@ssh-client: Check key files generated:  
    
    `ls -l ~/.ssh/`

    ```
    total 8
    -rw------- 1 root root 1766 Mar 24 11:33 id_rsa
    -rw-r--r-- 1 root root  402 Mar 24 11:33 id_rsa.pub
    ```

 3. rik@ssh-client: Create (if missing) ~/.ssh/authorized_keys file on ssh-server for the user bob (require bob's password):  

    `ssh bob@ssh-server "mkdir -p ~/.ssh && touch ~/.ssh/authorized_keys && chmod 700 ~/.ssh && chmod 640 ~/.ssh/authorized_keys"`

    ```
    bob@ssh-server's password:
    ```

4. rik@ssh-client: Append the 'ssh-client public key' to 'ssh-server authorized keys' on ssh-server (require bob's password):

    `cat ~/.ssh/id_rsa.pub | ssh bob@ssh-server "cat >> ~/.ssh/authorized_keys"`

    ```
    bob@ssh-server's password:
    ```

5. rik@ssh-client: Check that now ssh login as bob@ssh-server work without password:

    `ssh bob@ssh-server "pwd"`

    ```
    /home/bob
    ```
