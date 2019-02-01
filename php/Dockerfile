FROM php:7.2-fpm

#ARG SYMFONY_ENV=dev

ADD config/xdebug.ini /usr/local/etc/php/conf.d/xdebug.ini
COPY config/php.ini /usr/local/etc/php/php.ini

EXPOSE 9000

WORKDIR /var/www/html
