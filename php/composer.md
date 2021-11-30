# PHP Development: Composer

## Composer Useful Commands

| command                                                      | description                                           |
|--------------------------------------------------------------|-------------------------------------------------------|
| `composer clearcache && rm -rf vendor/* && rm composer.lock` | Clear all                                             |
| `composer dump-autoload`                                     | Generate autoload                                     |
| `composer install`                                           | Install all packages                                  |
| `composer update`                                            | Update all packages                                   |
| `composer show <package-name>`                               | Show <package-name> package version                   |
| `composer require <package-name>`                            | Install <package-name> package as production package  |
| `composer require --dev <package-name>`                      | Install <package-name> package as develop package     |
