# VSCode Development Environment for PHP (with Docker & WSL2)

## Create Project

 1. Open Ubuntu Terminal (WSL2)  
 2. Create project folder (from Ubuntu Terminal)  
`mkdir -p ~/workspace/project`
`cd ~/workspace/project && code .`  

### Create PHP empty Project

 1. Open project folder WSL from VSCode  
_Remote WSL: Open Folder in WSL..._  
 2. Add Development Container  
_Remote-Containers: Add Development Container Configuration Files..._ > _PHP_ > 8_  
 3. Reopen in Container  
_Remote-Containers: Reopen in Container_
 4. Check Installed Extensions (CTRL + SHIFT + X)  
_PHP Debug (1.14.11)_  
_PHP Intelephense (1.6.3)_  

Optional:

- Install PHPUnit  

#### Install PHP-CS-Fixer

`mkdir --parents tools/php-cs-fixer`  
`composer require --working-dir=tools/php-cs-fixer friendsofphp/php-cs-fixer`  

### Create PHP empty Symfony Project

 1. Open project folder WSL from VSCode  
_Remote WSL: Open Folder in WSL..._  
 2. Add Development Container  
_Remote-Containers: Add Development Container Configuration Files..._ > _PHP & MariaDB (community)_  
 3. Reopen in Container  
_Remote-Containers: Reopen in Container_
 4. Check Installed Extensions (CTRL + SHIFT + X)  
_PHP Debug (1.14.11)_  
_PHP IntelliSense (2.3.14)_  
_SQLTools (0.23.0)_  
_SQLTools MySQL/MariaDB (0.2.0)_  
 5. Create Symfony Project  
_Terminal_ > _New Terminal_
`composer create-project symfony/website-skeleton www`  
 6. Run the Web Server  
`cd www/public`  
`php -S localhost:8080`  
 7. Configure Tasks (to Run the Web Server)  
./vscode/tasks.json  

## Appendix

### Prerequisites

- [VS Code](https://code.visualstudio.com/docs/setup/windows)
- [Docker Desktop on Windows](https://docs.docker.com/docker-for-windows/install/)
- [Windows Subsystem for Linux](https://docs.microsoft.com/windows/wsl) (Ubuntu 20.04 LTS)
- [Windows Terminal](https://docs.microsoft.com/en-us/windows/terminal/get-started) (Recommended but not required)

### References

- [https://code.visualstudio.com/docs/remote/remote-overview]
- [https://dev.to/jnous5/setting-up-a-local-development-environment-using-vs-code-docker-and-wsl-2-5c0i]
- [https://blog.theodo.com/2019/07/vscode-php-development/]
- [https://code.visualstudio.com/docs/languages/php]
- [https://dev.to/manuelojeda/setup-your-vscode-as-php-code-editor-ide-46g1]
- [http://shanalikhan.github.io/2015/12/15/Visual-Studio-Code-Sync-Settings.html]
