ARG VERSION
FROM php:${VERSION}-fpm

RUN apt-get update \
    && apt-get install -y libfreetype6-dev libjpeg62-turbo-dev libpng-dev git vim \
    && docker-php-ext-install -j$(nproc) mysqli pdo_mysql gd bcmath zip

RUN curl -s http://getcomposer.org/installer | php && \
    echo "export PATH=${PATH}:/var/www/vendor/bin" >> ~/.bashrc && \
    mv composer.phar /usr/local/bin/composer && \
    composer config -g repo.packagist composer https://packagist.laravel-china.org

RUN . ~/.bashrc
