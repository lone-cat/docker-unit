FROM php:7.4-apache
MAINTAINER Alex <alex@melentev.net>

RUN a2enmod rewrite
RUN a2enmod macro

RUN curl -sS https://getcomposer.org/installer -o /tmp/composer-setup.php
RUN php /tmp/composer-setup.php --install-dir=/usr/local/bin --filename=composer

RUN apt-get update \
    && apt-get install -y wget git unzip \
    && pecl install xdebug-2.9.4 \
    && docker-php-ext-enable xdebug

RUN docker-php-ext-install mysqli && docker-php-ext-enable mysqli

RUN docker-php-ext-install pdo pdo_mysql && docker-php-ext-enable pdo pdo_mysql

RUN wget https://get.symfony.com/cli/installer -O - | bash
RUN mv /root/.symfony/bin/symfony /usr/local/bin/symfony

COPY conf/apache2.conf /etc/apache2/apache2.conf
COPY conf/envvars /etc/apache2/envvars
COPY conf/magic /etc/apache2/magic
COPY conf/ports.conf /etc/apache2/ports.conf

COPY conf/sites-enabled /etc/apache2/sites-enabled
COPY conf/conf-enabled /etc/apache2/conf-enabled

ENV XDEBUG_CONFIG="remote_host=host.docker.internal remote_enable=1 extended_info=1"
ENV PHP_IDE_CONFIG="serverName=Docker"

WORKDIR /app

