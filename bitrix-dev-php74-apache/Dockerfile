FROM php:7.4-apache

COPY php.ini "$PHP_INI_DIR/php.ini"

# https://hub.docker.com/_/php

# interbase soap

RUN apt update && apt install -y --no-install-recommends \
      libmcrypt-dev \
      libzip-dev \
      libpng-dev \
      libjpeg-dev \
      libwebp-dev \
    && echo '' | pecl install mcrypt \
    && pecl install xdebug \
    && docker-php-source extract \
    && docker-php-ext-configure mysqli \
    && docker-php-ext-install mysqli \
    && docker-php-ext-configure gd \
    && docker-php-ext-install gd \
#    && docker-php-ext-configure imagick \
#    && docker-php-ext-install imagick \
    && docker-php-ext-configure opcache \
    && docker-php-ext-install opcache \
    && docker-php-ext-configure zip \
    && docker-php-ext-install zip \
#    && docker-php-ext-configure memcache \
#    && docker-php-ext-install memcache \
#    && docker-php-ext-configure memcached \
#    && docker-php-ext-install memcached \
    && docker-php-source delete \
    && apt clean; rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* /usr/share/doc/* \
    && echo "DONE"

COPY apache2/sites-available/000-default.conf /etc/apache2/sites-available/000-default.conf

WORKDIR "/var/www/bitrix"

EXPOSE 80
