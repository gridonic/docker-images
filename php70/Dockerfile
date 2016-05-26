FROM php:7.0

MAINTAINER Peter Siska "pesche@gridonic.ch"

COPY config/custom.ini /usr/local/etc/php/conf.d/

RUN apt-get update && apt-get install -yqq --no-install-recommends zlib1g-dev libicu-dev libpq-dev \
    && docker-php-ext-install opcache \
    && docker-php-ext-install intl \
    && docker-php-ext-install mbstring \
    && docker-php-ext-install pdo_mysql \
    && docker-php-ext-install pdo_pgsql \
    && docker-php-ext-install zip \
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
