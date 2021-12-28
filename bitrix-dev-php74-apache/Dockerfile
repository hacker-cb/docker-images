FROM php:7.4-apache

COPY php.ini "$PHP_INI_DIR/php.ini"

# https://hub.docker.com/_/php

RUN apt update && apt install -y  \
      libmcrypt-dev \
    && echo '' | pecl install mcrypt \
    && pecl install xdebug \
    && docker-php-source extract \
    && docker-php-ext-configure mysqli \
    && docker-php-ext-install mysqli \
    && docker-php-source delete \
    && apt clean; rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* /usr/share/doc/* \
    && echo "DONE"

COPY apache2/sites-available/000-default.conf /etc/apache2/sites-available/000-default.conf

WORKDIR "/var/www/bitrix"

EXPOSE 80
