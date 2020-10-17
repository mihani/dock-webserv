FROM php:8.0.0RC2-fpm-alpine

ENV APCU_VERSION 5.1.19
ENV XDEBUG_VERSION 2.9.8
ENV COMPOSER_VERSION 2.0.0-RC2
ENV PICKLE_VERSION 0.6.0

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
        docker-php-ext-install intl zip

RUN wget https://github.com/FriendsOfPHP/pickle/releases/download/v${PICKLE_VERSION}/pickle.phar && mv pickle.phar /usr/local/bin/pickle && \
    chmod +x /usr/local/bin/pickle && \
    pickle install xdebug-${XDEBUG_VERSION} && \
    pickle install apcu-${APCU_VERSION} && \
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
