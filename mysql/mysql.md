# mysql

## Install MySQL

```bash
sudo apt -y install mysql-server
mysql --version
```

```console
mysql  Ver 8.0.37-0ubuntu0.22.04.3 for Linux on x86_64 ((Ubuntu))
```

## Config MySQL to accept remote connections

```bash
vi /etc/mysql/mysql.conf.d/mysqld.cnf
```

```console
# bind-address          = 127.0.0.1
# mysqlx-bind-address   = 127.0.0.1
```

## Show users and plugins

```bash
mysql -e "SELECT user, host, plugin FROM mysql.user;"
```

```console
+------------------+-----------+-----------------------+
| user             | host      | plugin                |
+------------------+-----------+-----------------------+
| debian-sys-maint | localhost | caching_sha2_password |
| mysql.infoschema | localhost | caching_sha2_password |
| mysql.session    | localhost | caching_sha2_password |
| mysql.sys        | localhost | caching_sha2_password |
| root             | localhost | auth_socket           |
+------------------+-----------+-----------------------+
```

### User plugins explanation

| plugin                  | description                                                  |
|-------------------------|--------------------------------------------------------------|
| `auth_socket`           | Default plugin (without password) for root (only @localhost) |
| `caching_sha2_password` | Default plugin (with password)                               |
| `mysql_native_password` | Legacy plugin (with password) - **not recommended**          |

## Change password for user root

```bash
mysql -e <<<SQL
CREATE USER '<user>' IDENTIFIED WITH caching_sha2_password BY '<password>';
GRANT ALL PRIVILEGES ON *.* TO '<user>' WITH GRANT OPTION;
FLUSH PRIVILEGES;
SQL
```

In the above command replace `<password>` with the root password, and `<user>` with:

- root'@'localhost for root user on local host
- root'@''@'%'     for root user on remote hosts

## Enable root login (with password) for any local (@localhost) and remote ('@%') hosts

```bash
mysql -e <<<SQL
CREATE USER 'root'@'%' IDENTIFIED WITH caching_sha2_password BY '<password>';
GRANT ALL PRIVILEGES ON *.* TO 'root'@'%' WITH GRANT OPTION;
DROP USER 'root'@'localhost';
FLUSH PRIVILEGES;
SELECT user, host, plugin FROM mysql.user;
```

```console
+------------------+-----------+-----------------------+
| user             | host      | plugin                |
+------------------+-----------+-----------------------+
| root             | %         | mysql_native_password |
| debian-sys-maint | localhost | caching_sha2_password |
| mysql.infoschema | localhost | caching_sha2_password |
| mysql.session    | localhost | caching_sha2_password |
| mysql.sys        | localhost | caching_sha2_password |
+------------------+-----------+-----------------------+
```

## Login from shell without username/password for any user

Create `~/.my.cnf` with right permissions, replacing `<username>` and `<password>`:

```bash
vi ~/.my.cnf && chmod 600 ~/.my.cnf
```

```console
[client]
user=<username>
password=<password>
```

## Backup and Restore

### Backup using `mysqldump`

mysqldump base command example:

`mysqldump -u <user> -p <db> ... > db-dump.sql`

| command                                                      | description                          |
|--------------------------------------------------------------|--------------------------------------|
| `mysqldump --no-data`                                        | Dump all tables structure and data   |
| `mysqldump <tablename>`                                      | Dump single table structure and data |
| `mysqldump --no-data`                                        | Dump only all tables schema          |
| `mysqldump --no-create-info --skip-triggers --skip-routines` | Dump only all tables data            |

### Restore using `mysql` (in background)

```bash
tar -xzvf db-dump.tar.gz
mysql -e "CREATE DATABASE db;"
# mysql db < db-dump.sql
nohup mysql db < db-dump.sql > db-restore.log 2>&1 &
mysql db -e "SHOW TABLES;" && tail db-restore.log
```

```console
[1] 116972
...
[1]+  Done                    nohup mysql ...
```
