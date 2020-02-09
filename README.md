# Docker webserver

## Use Repository

1. Clone this repository
2. Rename folder if you want
3. Start docker

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
