FROM php:7.2-fpm-alpine3.8

USER root

RUN apk --no-cache update \
    && apk --no-cache upgrade \
    && apk --no-cache add shadow \
    && usermod -u 1000 www-data

RUN apk --no-cache add --virtual libmcrypt-dev freetype-dev libxml2-dev \
    && docker-php-source extract \
    && docker-php-ext-install \
    bcmath \
    mysqli \
    pdo pdo_mysql \
    && docker-php-source delete

COPY ./laravel.ini /usr/local/etc/php/conf.d
COPY ./xlaravel.pool.conf /usr/local/etc/php-fpm.d

WORKDIR /var/www


EXPOSE 9000

CMD ["php-fpm"]
