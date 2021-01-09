FROM php:7.4.7-apache

ARG TZ
ENV COMPOSER_ALLOW_SUPERUSER 1

COPY --from=composer /usr/bin/composer /usr/bin/composer
COPY ./000-default.conf /etc/apache2/sites-available/
COPY ./php.ini /usr/local/etc/php

RUN apt-get update && apt-get install -y git unzip &&  \
docker-php-ext-install bcmath pdo_mysql opcache && pecl install xdebug && \
docker-php-ext-enable xdebug && \
mv /etc/apache2/mods-available/rewrite.load /etc/apache2/mods-enabled

RUN /bin/sh -c a2enmod rewrite
