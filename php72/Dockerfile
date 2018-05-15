FROM php:7.2-cli

MAINTAINER Peter Siska "pesche@gridonic.ch"

COPY config/99_custom.ini /usr/local/etc/php/conf.d/

RUN apt-get update && apt-get install -y \
        git \
        curl \
        zlib1g-dev \
        libicu-dev \
        libpq-dev \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libmcrypt-dev \
        libpng-dev \
        libmagickwand-dev \
 && docker-php-ext-configure \
        gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
 && docker-php-ext-install -j$(nproc) \
        gd \
        opcache \
        intl \
        mbstring \
        pdo_mysql \
        pdo_pgsql \
        zip \
        iconv \
 && pecl install \
        apcu-5.1.8 \
        imagick \
        mcrypt-1.0.1 \
 && docker-php-ext-enable \
        apcu \
        imagick \
        mcrypt \
 && apt-get -y clean \
 && rm -rf /var/lib/apt/lists/*
