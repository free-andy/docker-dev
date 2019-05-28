ARG VERSION
FROM php:${VERSION}-fpm

RUN apt-get update \
    && apt-get install -y libfreetype6-dev libjpeg62-turbo-dev libpng-dev \
    && docker-php-ext-install -j$(nproc) mysqli pdo_mysql gd bcmath zip

EXPOSE 9000
