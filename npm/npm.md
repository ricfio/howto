# NPM

## NPM useful commands

| command                                  | description                                                         |
|------------------------------------------|---------------------------------------------------------------------|
| `npm -v`                                 | Show NPM version                                                    |
| `npm list [-g]`                          | List the installed packages (-g for global)                         |
| `npm outdated [-g]`                      | List the outdated packages  (-g for global)                         |
| `npm install`                            | Install all packages (local installation)                           |
| `npm install [-g] <package>[@<version>]` | Install a specific package `<version>` (-g for global installation) |
| `npm uninstall`                          |                                                                     |
| `npm remove`                             |                                                                     |
| `npm update [-g]`                        | Update outdated packages    (-g for global)                         |
| `npm run`                                | List the scripts available                                          |
| `npm start`                              |                                                                     |
| `npm audit`                              |                                                                     |
| `npm view <package> version`             | Show the latest version of a `<package>`                            |
| `npm view <package> versions`            | Show the available versions of a `<package>`                        |

## NPM semantic versioning

The table show how to specify acceptable version ranges up to 1.0.4 (for example):

| releases       | version syntax         | rule                                                               |
|----------------|------------------------|--------------------------------------------------------------------|
| Major releases | * or x                 | Increment the first digit and reset middle and last digits to zero |
| Minor releases | 1 or 1.x or ^1.0.4     | Increment the middle digit and reset last digit to zero            |
| Patch releases | 1.0 or 1.0.x or ~1.0.4 | Increment the third digit                                          |
