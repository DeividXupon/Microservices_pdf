FROM php:7.4-fpm

# Installing dependencies for Laravel to decompress Composer
RUN apk add --no-cache \
    bash \
    curl \
    libpng-dev \
    libzip-dev \
    zlib-dev

# PHP extensions
RUN docker-php-ext-install \
    && docker-php-ext-install zip

# Composer
COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

RUN apk add --no-cache nodejs npm

WORKDIR /var/www

EXPOSE 9000
