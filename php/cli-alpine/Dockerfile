FROM php:7.2-cli-alpine3.8

USER root

RUN pecl channel-update pecl.php.net \
    && addgroup -g 1000 cli \
    && adduser -u 1000 -S cli cli

RUN apk --no-cache update \
    && apk --no-cache upgrade

RUN apk --no-cache add --virtual libmcrypt-dev freetype-dev libxml2-dev \
    && docker-php-source extract \
    && docker-php-ext-install \
    bcmath \
    mysqli \
    pdo pdo_mysql \
    && docker-php-source delete \
    && apk --no-cache add curl git openssh \
    && curl -sSL https://getcomposer.org/installer | php -- --install-dir=/usr/bin --filename=composer

RUN mkdir /var/www \
    && chown -R cli:cli /var/www

USER cli

WORKDIR /var/www

