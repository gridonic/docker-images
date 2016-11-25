FROM php:7.0-cli

MAINTAINER Peter Siska "pesche@gridonic.ch"

COPY config/custom.ini /usr/local/etc/php/conf.d/

RUN apt-get update && apt-get install -yqq --no-install-recommends \
    zlib1g-dev \
    libicu-dev \
    libpq-dev \
    libfreetype6-dev \
    libjpeg62-turbo-dev \
    libmcrypt-dev \
    libpng12-dev \
    && docker-php-ext-install -j$(nproc) opcache \
    && docker-php-ext-install -j$(nproc) intl \
    && docker-php-ext-install -j$(nproc) mbstring \
    && docker-php-ext-install -j$(nproc) pdo_mysql \
    && docker-php-ext-install -j$(nproc) pdo_pgsql \
    && docker-php-ext-install -j$(nproc) zip \
    && docker-php-ext-install -j$(nproc) iconv \
    && docker-php-ext-install -j$(nproc) mcrypt \
    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install -j$(nproc) gd \
    && rm -r /var/lib/apt/lists/*

# Install git and curl
RUN apt-get update && apt-get install -yqq --no-install-recommends git curl \
    && rm -r /var/lib/apt/lists/*

# APCu
RUN pecl install apcu-5.1.3 \
    && docker-php-ext-enable apcu

# Imagick
RUN apt-get update && apt-get install -yqq --no-install-recommends libmagickwand-dev \
    && pecl install imagick \
    && docker-php-ext-enable imagick

# Clean up
RUN apt-get -y clean \
    && rm -r /var/lib/apt/lists/*
