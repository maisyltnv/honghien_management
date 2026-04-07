FROM php:8.1-fpm-alpine

RUN apk add --no-cache \
    icu-dev \
    oniguruma-dev \
    libzip-dev \
    libxml2-dev \
    libpng-dev \
    libjpeg-turbo-dev \
    freetype-dev \
    bash \
    && docker-php-ext-configure gd --with-freetype --with-jpeg \
    && docker-php-ext-install -j$(nproc) mysqli pdo_mysql mbstring intl zip gd xml opcache

COPY docker/php/php.ini /usr/local/etc/php/conf.d/zzz-custom.ini

WORKDIR /var/www/html

RUN addgroup -g 1000 -S app && adduser -u 1000 -S app -G app \
    && chown -R app:app /var/www/html

USER app

