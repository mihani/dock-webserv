# Docker webserver

This repo allow to install php and dependency to start project or clone so fast.

## Test Status

Each version is tested on build step but it isn't already test with project.

**This version is not tested in project**

## Images, Main Dependancies version

* PHP : 8.0.0
* Composer : 2.0.8
* XDebug : 3.0.2
* Docker compose : 3.7

## How use it ?

1. Clone repo
1. Chose your favorite branch and/or tag
1. Change `docker.env` variables and config `docker-compose.yml`
1. If you would like docker bash history run `touch docker/data/history` before docker up.
1. Run `docker-compose up -d`
1. Change git remote to versionning your project
```bash
$ git remote set-url --delete origin git@github.com:mihani/dock-webserv.git
$ git remote set-url --add origin <your-repository> 
```

## Branch description

* `master` : docker-compose with php only
* `composer-1` : docker-compose with php only and composer 1
* `php-nginx` : docker compose with php and nginx only
* `php-nginx-mysql` : docker compose with mysql, php and nginx
