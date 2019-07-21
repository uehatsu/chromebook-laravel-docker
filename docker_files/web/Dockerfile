FROM php:7.2-apache

RUN apt-get update \
 && apt-get upgrade -y \
 && pecl install xdebug \
 && docker-php-ext-enable xdebug \
 && echo 'xdebug.remote_enable = On' >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini \
 && echo 'xdebug.remote_autostart = On' >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini \
 && echo 'xdebug.remote_connect_back = Off' >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini \
 && echo 'xdebug.remote_host = docker.for.mac.localhost' >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini \
 && echo 'xdebug.remote_port=9001' >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini \
 && echo 'xdebug.idekey="phpstorm"' >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini \
 && apt-get install -y git rsync vim less zip unzip libxml2-dev zlib1g-dev \
 && docker-php-ext-install pdo_mysql soap intl zip \
 && curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer \
 && rm -rf /tmp/*
RUN a2enmod rewrite

RUN useradd -u 1000 -m docker
ENV APACHE_RUN_USER docker
ENV APACHE_RUN_GROUP docker

ENV COMPOSER_ALLOW_SUPERUSER 1
ENV COMPOSER_HOME /composer
ENV PATH $PATH:/composer/vendor/bin

WORKDIR /src
