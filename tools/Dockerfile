FROM php:7.2-cli

ARG SYMFONY_ENV=dev

RUN apt-get update && apt-get install -y \
    git \
    zip \
    unzip

RUN pecl install -o -f xdebug-2.6.0 \
    && rm -rf /tmp/pear

# Installation de composer
RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" \
    && php composer-setup.php --install-dir=/usr/local/bin --filename=composer \
    && php -r "unlink('composer-setup.php');"

# Assign a shell to user www-data
RUN chsh -s /bin/bash www-data

# Access right
RUN mkdir -p /var/www/html && chown -R www-data:www-data /var/www/html

# copy Configuration files
ADD config/xdebug.ini /usr/local/etc/php/conf.d/xdebug.ini
COPY config/php.ini /usr/local/etc/php/php.ini

WORKDIR /var/www/html
