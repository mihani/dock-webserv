FROM php:7.4.2-fpm-alpine

ENV APCU_VERSION 5.1.18
ENV XDEBUG_VERSION 2.9.2
ENV COMPOSER_VERSION 1.9.3

RUN apk add --update --no-cache \
        bash \
        ca-certificates \
        git \
        icu-libs \
        libxml2-dev \
        unzip \
        zip \
        oniguruma-dev \
        libzip-dev && \
    apk add --update --no-cache --virtual .build-deps \
        $PHPIZE_DEPS \
        icu-dev && \
    pecl install apcu-${APCU_VERSION} xdebug-${XDEBUG_VERSION} && \
    docker-php-ext-install intl zip && \
    docker-php-ext-enable opcache apcu xdebug && \
    apk del .build-deps && \
    apk add gosu --update --no-cache --repository http://dl-3.alpinelinux.org/alpine/edge/testing/ && \
    addgroup bar && \
    adduser -D -h /home -s /bin/bash -G bar foo

# Composer
RUN curl -sS https://getcomposer.org/installer \
        | php -- --filename=composer --install-dir=/usr/local/bin --version=${COMPOSER_VERSION}

ADD entrypoint.sh /entrypoint
COPY config/php.ini /usr/local/etc/php/php.ini
COPY config/xdebug.ini /usr/local/etc/php/conf.d/debug.ini

WORKDIR /srv

ENTRYPOINT ["/entrypoint"]
