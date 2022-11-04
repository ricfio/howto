# GIT

## Clone a GIT Repository

```bash
git clone git@github.com:ricfio/howto.git
```

## Init a GIT Repository

```bash
echo "# README" >> README.md
git init
git add --all
git commit -m "Initial commit"
git branch -m main
```

## Add remote origin on GitHub

Choose between ssh or http autentication:

```bash
# Add remote origin on GitHub (use ssh autentication)
git remote add origin git@github.com:ricfio/howto.git
```

```bash
# Add remote origin on GitHub (use https autentication)
git remote add origin https://github.com/ricfio/howto.git
```

## Push main branch on GitHub Repository

```bash
git push -u origin main
```

## GIT Useful commands

### Common commands

| command                                            | description                                                    |
|----------------------------------------------------|----------------------------------------------------------------|
| `git clone <repo> <folder> -b <branch>`            | Clone `<repo>` into `<folder>` with checkout on `<branch>`     |
| `git fetch`                                        | Fetch from remote                                              |
| `git branch --list`                                | List local branches                                            |
| `git branch --list --remote`                       | List remote branches                                           |
| `git switch -c <branch> --track <remote>/<branch>` | Create and Switch to a new `<branch>` from `<remote>/<branch>` |
| `git checkout <branch>`                            | Checkout `<branch>`                                            |
| `git pull`                                         | Pull from remote                                               |
| `git log --pretty=oneline -n 5 [<from>..<to>]`     | Show the last 5 commits (one row for each one)                 |
| `git restore <files>`                              | Restore `<file>` or `<files>` (file1 .. fileN) from repository |
| `git push [-f] origin main`                        | Push from local to remote origin main branch (-f force)        |
| `git push origin --all`                            | Push from local to remote origin all branchs                   |
| `git push origin --tags`                           | Push from local to remote origin all tags                      |

### GIT-Flow commands

```bash
git flow init -d
```

| command                                       | description                                                         |
|-----------------------------------------------|---------------------------------------------------------------------|
| `git flow init -d`                            | Initialize repository for GIT Flow (`apt-get install git-flow`)     |
| `git flow feature start <feature> [<branch>]` | Start new `<feature>` from `<branch>`                               |
| `git flow feature finish <feature>`           | Finish `<feature>`                                                  |
| `git flow hotfix start <hotfix> [<branch>]`   | Start new hotfix `<hotfix>` from `<branch>`                         |

### Clean, Reset and Delete commands

| command                                       | description                                                         |
|-----------------------------------------------|---------------------------------------------------------------------|
| `git clean -nd`                               | Show local untracked files                                          |
| `git clean -fd`                               | Remove local untracked files and directories                        |
| `git reset --hard [<remote>/<branch>]`        | Hard reset local `<branch>` to `<remote>/<branch>`                  |
| `git branch -d <local-branch>`                | Delete local branch with limitations                                |
| `git branch -D <local-branch>`                | Delete local branch with force                                      |

### Submodules commands

| command                                       | description                                                         |
|-----------------------------------------------|---------------------------------------------------------------------|
| `git clone --recursive <repo> <folder>`       | Clone repository `<repo>` and its submodules into `<folder>`        |
| `git submodule update --init --recursive`     | Init submodules into `<repo>` cloned without `--recursive option`   |

### Minor commands

| command                                       | description                                                         |
|-----------------------------------------------|---------------------------------------------------------------------|
| `git config --unset core.autocrlf`            | Remove a configuration entry in the repository                      |
| `git config http.postBuffer 10485760`         | Update post buffer to 10MB                                          |

## GIT Global Configuration

These commands store your preferences in a file named .gitconfig inside your home directory (~ on UNIX and Mac, and %USERPROFILE% on Windows):  

```bash
git config --global color.ui "auto"
git config --global credential.helper 'cache --timeout=3600'
git config --global http.sslVerify true
git config --global init.defaultBranch main
git config --global user.name "Riccardo Fiorenza"
git config --global user.email "ricfio.professional@gmail.com"
```

If you’re on a Microsoft Windows, you would like:

- set core.autocrlf to true (converts LF endings into CRLF when you check out code)
- set core.filemode to false (ignores file permissions changing)

```bash
git config --global core.autocrlf true
git config --global core.filemode false
```
