FROM php:7.3.2-fpm

#build php extension layer
RUN export DEBIAN_FRONTEND=noninteractive \
    && apt-get update \ 
    && apt-get install -y \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libmcrypt-dev \
        libpng-dev \
        libicu-dev \
        libpq-dev \
        libxpm-dev \
        libvpx-dev \
        libzip-dev \
    && docker-php-ext-install -j$(nproc) gd \
    && docker-php-ext-install -j$(nproc) intl \
    && docker-php-ext-install -j$(nproc) zip \
    && docker-php-ext-install -j$(nproc) mysqli \
    && docker-php-ext-install -j$(nproc) pdo_mysql \
    && docker-php-ext-install -j$(nproc) exif \
    && docker-php-ext-configure gd \
        --with-freetype-dir=/usr/include/ \
        --with-jpeg-dir=/usr/include/ \
        --with-xpm-dir=/usr/lib/x86_64-linux-gnu/ \
        --with-vpx-dir=/usr/lib/x86_64-linux-gnu/ \
    && pecl install mcrypt-1.0.2 \
    && docker-php-ext-enable mcrypt 

VOLUME /usr/local/etc/php/php.ini

WORKDIR /var/www/html
