# Docker webserver

This repo allow to install php and dependency to start project or clone so fast.

## How use it ?

1. Clone repo
2. Chose your favorite branch and/or tag
3. Change `docker.env` variables and config `docker-compose.yml`
4. Run `docker-compose up -d`
5. Change git remote to versionning your project
```bash
$ git remote set-url --delete origin git@github.com:mihani/dock-webserv.git
$ git remote set-url --add origin <your-repository> 
```

## Branch description

* `master` : docker-compose with php only
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
