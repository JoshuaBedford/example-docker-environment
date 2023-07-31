FROM php:8-fpm

ARG DEBIAN_FRONTEND=noninteractive
RUN apt update \
    && apt install -y zlib1g-dev libzip-dev libpng-dev libmagickwand-dev libssl-dev pkg-config mariadb-client curl gnupg unzip\
    && docker-php-ext-install pdo_mysql zip gd \
    && php -r "readfile('http://getcomposer.org/installer');" | php -- --install-dir=/usr/bin/ --filename=composer \
    && pecl install redis \
    && docker-php-ext-enable redis \
    && pecl install mongodb \
    && docker-php-ext-enable mongodb \
    && pecl install imagick \
    && docker-php-ext-enable imagick \
    && mv "$PHP_INI_DIR/php.ini-development" "$PHP_INI_DIR/php.ini"
