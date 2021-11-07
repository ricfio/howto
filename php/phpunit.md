# PHPUnit

## Add PHPUnit with Composer

`composer require --dev phpunit/phpunit`  
`./vendor/bin/phpunit --version`  

composer.json  
```
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

## Update autoload
`composer dump-autoload`  

## Test Execution
`./vendor/bin/phpunit tests`  

## Test Execution with TestDox
`./vendor/bin/phpunit tests --testdox`  
