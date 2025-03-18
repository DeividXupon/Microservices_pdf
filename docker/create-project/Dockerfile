# Versão do PHP
ARG PHP_VERSION=latest

FROM php:${PHP_VERSION}

USER root

RUN apt-get update && apt-get install -y \
    curl \
    git \
    zip \
    unzip \
    libzip-dev \
    libpng-dev \
    libjpeg-dev \
    libfreetype6-dev \
    libonig-dev \
    && rm -rf /var/lib/apt/lists/*

WORKDIR /var/www

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# Usuário não-root para poder ter permissão de escrita
RUN chown -R 1000:1000 /var/www
USER 1000:1000

# Nome do projeto
ENV PROJECT_NAME=.

CMD ["sh", "-c", "composer create-project --prefer-dist laravel/laravel ${PROJECT_NAME}"]
