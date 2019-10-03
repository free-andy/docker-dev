ARG VERSION
FROM php:${VERSION}-fpm

# RUN cp /etc/apt/sources.list /etc/apt/sources.list.bak \
#     && echo 'deb https://mirrors.tuna.tsinghua.edu.cn/debian/ stretch main contrib non-free' > /etc/apt/sources.list \
#     && echo 'deb https://mirrors.tuna.tsinghua.edu.cn/debian/ stretch-updates main contrib non-free' >> /etc/apt/sources.list \
#     && echo 'deb https://mirrors.tuna.tsinghua.edu.cn/debian/ stretch-backports main contrib non-free' >> /etc/apt/sources.list \
#     && echo 'deb https://mirrors.tuna.tsinghua.edu.cn/debian-security stretch/updates main contrib non-free' >> /etc/apt/sources.list

RUN apt-get update \
    && apt-get install -y libfreetype6-dev libjpeg62-turbo-dev libpng-dev \
    && docker-php-ext-install -j$(nproc) mysqli pdo_mysql gd bcmath zip \
    && pecl install swoole \
    && docker-php-ext-enable swoole

RUN usermod -u 1000 www-data

EXPOSE 9000
