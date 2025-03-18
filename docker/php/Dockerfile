FROM php:7.4-fpm

# Installing dependencies for Laravel to decompress Composer
RUN apt-get update && apt-get install -y \
    bash \
    curl \
    libpng-dev \
    libzip-dev \
    zlib1g-dev \
    && rm -rf /var/lib/apt/lists/*

# PHP extensions
RUN docker-php-ext-install zip

# Composer
COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

RUN apt-get update && apt-get install -y nodejs npm && rm -rf /var/lib/apt/lists/*

WORKDIR /var/www

EXPOSE 9000
