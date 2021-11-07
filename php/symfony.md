# PHP Development: Symfony

/usr/local/bin/composer create-project symfony/skeleton /app/my_project  --no-interaction

OPPURE

Create Symfony Project in the current folder:

```bash
symfony new my_project_name --no-git
mv my_project_name/* .
mv my_project_name/.env .
mv my_project_name/.gitignore .
rmdir my_project_name
```

## Symfony Useful Commands

| command                                     | command description                            |
|---------------------------------------------|------------------------------------------------|
| `composer recipes`                          | See the status of your Symfony recipes         |
| `bin/console debug:router`                  | Show all routes                                |
| `bin/console list doctrine`                 | Doctrine Command List                          |
| `bin/console make:entity`                   | Make Entity                                    |
| `bin/console make:migration`                | Prepare database migrations                    |
| `bin/console doctrine:migrations:migrate`   | Execute database migrations                    |

## Checks

```bash
symfony check:requirements
symfony check:security
```

## Server

```bash
symfony server:start -d
symfony server:status
symfony server:stop
symfony server:log
```

## Cache

```bash
php bin/console cache:clear
```

## Routing

```bash
php bin/console debug:router
php bin/console debug:router app_lucky_number
php bin/console router:match /lucky/number/8
```

## Others useful commands

```bash
php bin/console debug:autowiring
```

## Install Packages

### Install Doctrine

```bash
composer require symfony/orm-pack
composer require --dev symfony/maker-bundle
```

```bash
vi .env
```

```conf
DATABASE_URL="sqlite:///%kernel.project_dir%/var/data.db"
```

```bash
./bin/console doctrine:database:create
```

Creating an Entity Class:

```bash
./bin/console make:entity
```

See:

- [Databases and the Doctrine ORM](https://symfony.com/doc/current/doctrine.html)

### Others useful packages

```bash
composer require --dev symfony/profiler-pack
```
