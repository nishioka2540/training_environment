FROM php:8.1-fpm
SHELL ["/bin/bash", "-oeux", "pipefail", "-c"]

ENV COMPOSER_ALLOW_SUPERUSER=1 \
    COMPOSER_HOME=/composer

COPY --from=composer:1.10 /usr/bin/composer /usr/bin/composer

RUN \
    apt-get update && \
    apt-get -y install git unzip libzip-dev libicu-dev libonig-dev libfreetype6-dev libjpeg62-turbo-dev libpng-dev && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/* && \
    docker-php-ext-install intl pdo_mysql bcmath opcache && \
    pecl install xdebug-3.1.0 \
    && docker-php-ext-enable xdebug
    
COPY ./php.ini /usr/local/etc/php/php.ini
WORKDIR /work


