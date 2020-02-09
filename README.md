# Docker webserver

This repo allow to install php and dependency to start project or clone so fast.

## Test Status

Each version is tested on build step but it isn't already test with project.

**This version is not tested in project**

## Images, Main Dependancies version

* PHP : 7.4.13
* Composer : 2.0.8
* XDebug : 3.0.2
* Docker compose : 3.7
* Nginx 1.15.9
* Mysql : 8.0

## How use it ?

1. Clone repo
1. Chose your favorite branch and/or tag
1. Change `docker.env` variables
1. If you would like docker bash history run `touch docker/data/history` before docker up.
1. Run `docker-compose up -d`
1. Change git remote to versionning your project
```bash
$ git remote set-url --delete origin git@github.com:mihani/dock-webserv.git
$ git remote set-url --add origin <your-repository> 
```

## Branch description

* `master` : docker-compose with php only and composer 2
* `only-php-8` : docker-compose with php 8 only and composer 2
* `composer-1` : docker-compose with php only and composer 1
* `php-nginx` : docker compose with php and nginx only
* `php-nginx-mysql` : docker compose with mysql, php and nginx


## Mysql:8.0

Since Mysql 8.0 a new default authentification plugin used but there are few problem with.
The solution is config your mysql and ALTER or CREATE user with old authentification plugin.

1. Change the default plugin in `my.cnf`

```
[mysqld]
default_authentication_plugin=mysql_native_password
```

2. CREATE or ALTER user

*Here create version used*

```sql
CREATE USER 'nativeuser'@'localhost' IDENTIFIED WITH mysql_native_password BY 'password';
```

The branch `php-nginx` and `php-nginx-mysql` based on master, if you need composer 1 need create merge one or the other of the branch with `composer-1` branch.
