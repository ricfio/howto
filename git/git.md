# GIT

## GIT Useful commands

### Common commands

| command                                       | description                                                         |
|-----------------------------------------------|---------------------------------------------------------------------|
| `git init`                                    | Initialize repository                                               |
| `git add --all`                               | Add all new files                                                   |
| `git clone {REPO} {FOLDER} -b {BRANCH}`       | Clone repository {REPO} into {FOLDER} with checkout on {BRANCH}     |
| `git checkout {BRANCH}`                       | Checkout {BRANCH}                                                   |
| `git fetch`                                   | Fetch from remote                                                   |
| `git pull`                                    | Pull from remote                                                    |
| `git push [-f] origin main`                   | Push from local to remote main branch (-f option to force)          |
| `git log --pretty=oneline -n 3`               | Show the last 3 commits (one row for each one)                      |

### GIT-Flow, Clean, Reset and Delete commands

| command                                       | description                                                         |
|-----------------------------------------------|---------------------------------------------------------------------|
| `git flow init -d`                            | Initialize repository for GIT Flow (`apt-get install git-flow`)     |
| `git flow feature start {FEATURE} [{BRANCH}]` | Start new feature {FEATURE} from {BRANCH}                           |
| `git flow feature finish {FEATURE}`           | Finish feature {FEATURE}                                            |
| `git flow hotfix start {HOTFIX} [{BRANCH}]`   | Start new hotfix {HOTFIX} from {BRANCH}                             |
| `git clean -nd`                               | Show local untracked files                                          |
| `git clean -fd`                               | Remove local untracked files and directories                        |
| `git reset --hard [<origin/{BRANCH}>]`        | Hard reset local {BRANCH} to remote origin/{BRANCH}                 |
| `git branch -d <local-branch>`                | Delete local branch with limitations                                |
| `git branch -D <local-branch>`                | Delete local branch with force                                      |

### Submodules commands

| command                                       | description                                                         |
|-----------------------------------------------|---------------------------------------------------------------------|
| `git clone --recursive {REPO} {FOLDER}`       | Clone repository {REPO} into {FOLDER} with submodules cloning also  |
| `git submodule update --init --recursive`     | Initialize submodules into {REPO} cloned without --recursive option |

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

If you’re on a Microsoft Windows:

- set core.autocrlf to true (converts LF endings into CRLF when you check out code)
- set core.filemode to false (ignores file permissions changing)

```bash
git config --global core.autocrlf true
git config --global core.filemode false
```

## Create a new GIT Repository

```bash
echo "# example" >> README.md
git init
git config core.autocrlf false
git add --all
git commit -m "Initial commit"
git branch -m main
```

## Initialize repository for GIT Flow

```bash
git flow init -d
```

## Push main branch on GitHub Repository

```bash
git remote add origin https://github.com/ricfio/howto.git
git push -u origin main
```
