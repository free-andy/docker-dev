ARG VERSION
FROM php:${VERSION}-fpm

# RUN cp /etc/apt/sources.list /etc/apt/sources.list.bak \
#     && echo 'deb https://mirrors.tuna.tsinghua.edu.cn/debian/ stretch main contrib non-free' > /etc/apt/sources.list \
#     && echo 'deb https://mirrors.tuna.tsinghua.edu.cn/debian/ stretch-updates main contrib non-free' >> /etc/apt/sources.list \
#     && echo 'deb https://mirrors.tuna.tsinghua.edu.cn/debian/ stretch-backports main contrib non-free' >> /etc/apt/sources.list \
#     && echo 'deb https://mirrors.tuna.tsinghua.edu.cn/debian-security stretch/updates main contrib non-free' >> /etc/apt/sources.list

Run apt-get update \
    && apt-get install -y libfreetype6-dev libjpeg62-turbo-dev libpng-dev git vim zip \
    && docker-php-ext-install -j$(nproc) mysqli pdo_mysql gd bcmath zip \
    && pecl install swoole \
    && docker-php-ext-enable swoole

RUN curl -s http://getcomposer.org/installer | php \
    && echo "export PATH=${PATH}:/var/www/vendor/bin" >> ~/.bashrc \
    && mv composer.phar /usr/local/bin/composer \
    && composer config -g repo.packagist composer https://packagist.laravel-china.org

RUN . ~/.bashrc
