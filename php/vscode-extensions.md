# VSCode Development Extensions for PHP

## Remote Development

SSH, WSL, Containers:  
[https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.vscode-remote-extensionpack]

## [PHP Debug](https://marketplace.visualstudio.com/items?itemName=felixfbecker.php-debug) (1.14.11)

First, you should check your "PHP with Xdebug" installation:  
`php -v`  

```bash
vscode ➜ /workspaces/project $ php -v
PHP 8.0.1 (cli) (built: Jan 12 2021 01:48:33) ( NTS )
Copyright (c) The PHP Group
Zend Engine v4.0.1, Copyright (c) Zend Technologies
    with Xdebug v3.0.2, Copyright (c) 2002-2021, by Derick Rethans
```

.vscode/launch.json  

```json
{
    // Use IntelliSense to learn about possible attributes.
    // Hover to view descriptions of existing attributes.
    // For more information, visit: https://go.microsoft.com/fwlink/?linkid=830387
    "version": "0.2.0",
    "configurations": [
        {
            "name": "Listen for Xdebug",
            "type": "php",
            "request": "launch",
            "port": 9000
        },
        {
            "name": "Launch currently open script",
            "type": "php",
            "request": "launch",
            "program": "${file}",
            "cwd": "${fileDirname}",
            "port": 9000
        }
    ]
}
```

## [PHP Intelephense](https://marketplace.visualstudio.com/items?itemName=bmewburn.vscode-intelephense-client) (1.6.3)

1. Install Extension
2. Disable basic suggestions
3. Enable autocomplete in comments / annotations
4. Allow autocomplete in tests

.vscode/settings.json  

```json
{
    "editor.quickSuggestions": {
        "comments": true
    },
    "intelephense.files.exclude": [
        "**/.git/**",
        "**/.svn/**",
        "**/.hg/**",
        "**/CVS/**",
        "**/.DS_Store/**",
        "**/node_modules/**",
        "**/bower_components/**",
        "**/vendor/**/{Tests,tests}/**/*Test.php",
        "**/.history/**",
        "**/vendor/**/vendor/**"
    ],
    "php.suggest.basic": false,
    "php.validate.executablePath": "/usr/local/bin/php",
}
```

## [PHP-CS-Fixer](https://marketplace.visualstudio.com/items?itemName=junstyle.php-cs-fixer)

`mkdir -p tools/php-cs-fixer`  
`composer require --working-dir=tools/php-cs-fixer friendsofphp/php-cs-fixer`  

.vscode/settings.json  

```json
{
    "[php]": {
        "editor.defaultFormatter": "junstyle.php-cs-fixer",
        "editor.formatOnSave": true
    },
    "php-cs-fixer.rules": "@PhpCsFixer",
    "php-cs-fixer.executablePath": "/tools/php-cs-fixer/vendor/bin/php-cs-fixer",
    "php-cs-fixer.onsave": true,
    "php-cs-fixer.config": ".php_cs;.php_cs.dist",
    "php-cs-fixer.allowRisky": false,
    "php-cs-fixer.pathMode": "override",
    "php-cs-fixer.exclude": [],
    "php-cs-fixer.autoFixByBracket": true,
    "php-cs-fixer.autoFixBySemicolon": false,
    "php-cs-fixer.formatHtml": false,
    "php-cs-fixer.documentFormattingProvider": true
}
```

## [Psalm](https://marketplace.visualstudio.com/items?itemName=getpsalm.psalm-vscode-plugin)

The latest version of Psalm requires PHP >= 7.1 and Composer:  
`composer require --dev vimeo/psalm`  

Generate a config file:  
`./vendor/bin/psalm --init`  

Run Psalm:  
`./vendor/bin/psalm`  

References:  

- [Psalm Get Started](https://psalm.dev/docs/running_psalm/installation/)

## [PHP Getters & Setters](https://marketplace.visualstudio.com/items?itemName=phproberto.vscode-php-getters-setters)

1. Install Extension

## [Twig Language 2](https://marketplace.visualstudio.com/items?itemName=mblode.twig-language-2)

.vscode/settings.json  

```json
{
    "emmet.includeLanguages": {
        "twig": "html"
    }
}
```

## SQLTools

...

## Appendix

### References

- [https://code.visualstudio.com/docs/remote/remote-overview]
- [https://dev.to/jnous5/setting-up-a-local-development-environment-using-vs-code-docker-and-wsl-2-5c0i]
- [https://blog.theodo.com/2019/07/vscode-php-development/]
- [https://code.visualstudio.com/docs/languages/php]
- [https://dev.to/manuelojeda/setup-your-vscode-as-php-code-editor-ide-46g1]
- [http://shanalikhan.github.io/2015/12/15/Visual-Studio-Code-Sync-Settings.html]
