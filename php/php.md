# PHP

## Composer

| command                                                      | description                                              |
|--------------------------------------------------------------|----------------------------------------------------------|
| `composer init`                                              | Creates a basic composer.json file in current directory  |
| `composer clearcache && rm -rf vendor/* && rm composer.lock` | Clear all                                                |
| `composer dump-autoload`                                     | Generate autoload                                        |
| `composer install`                                           | Install all packages                                     |
| `composer update`                                            | Update all packages                                      |
| `composer show <package-name>`                               | Show `<package-name>` package version                    |
| `composer require <package-name>`                            | Install `<package-name>` package as production package   |
| `composer require --dev <package-name>`                      | Install `<package-name>` package as develop package      |

## [PHP Coding Standards Fixer](https://github.com/FriendsOfPHP/PHP-CS-Fixer)

### PHP-CS-Fixer Installation

```bash
mkdir --parents ~/tools/php-cs-fixer && cd $_ && composer require friendsofphp/php-cs-fixer
```

## PHPUnit

### Add PHPUnit with Composer

```bash
composer require --dev phpunit/phpunit
./vendor/bin/phpunit --version
cat composer.json
```

```console
{
  "require-dev": {
    "phpunit/phpunit": "^9.5"
  },
  "autoload": {
    "psr-4": {
      "App\\": "src/"
    }
  },
  "autoload-dev": {
    "psr-4": {
      "Tests\\": "tests/"
    }
  }
}
```

### Test Execution

`./vendor/bin/phpunit tests`  

### Test Execution with TestDox

`./vendor/bin/phpunit tests --testdox`  

## [PHP-Arkitect](https://github.com/phparkitect/arkitect)

### PHP-Arkitect Installation

```bash
mkdir --parents ~/tools/phparkitect && cd $_ && composer require phparkitect/phparkitect
```
