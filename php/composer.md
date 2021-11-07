# PHP Development: Composer

## Composer

Rebuild all:  
`composer clearcache && rm -rf vendor/* && rm composer.lock && composer install`  

Install production packages:  
`composer require <package-name>`  

Install develop packages:  
`composer require-dev <package-name>`  

Generating autoload:
`composer dump-autoload`  
