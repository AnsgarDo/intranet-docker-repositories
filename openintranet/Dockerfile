# syntax=docker/dockerfile:1

FROM composer:2.10.3 AS build

ARG OI_VERSION=1.11.0

COPY certs/*.crt /usr/local/share/ca-certificates/

RUN update-ca-certificates

RUN apk add --no-cache \
        ca-certificates \
        git \
        freetype-dev \
        libjpeg-turbo-dev \
        libpng-dev \
        libwebp-dev \
        libavif-dev \
    && docker-php-ext-configure gd \
        --with-avif \
        --with-freetype \
        --with-jpeg \
        --with-webp \
    && docker-php-ext-install -j"$(nproc)" gd

WORKDIR /src

RUN git clone --depth 1 --branch "${OI_VERSION}" \
    https://git.drupalcode.org/project/openintranet.git \
    /src/openintranet

WORKDIR /src/openintranet

RUN composer install \
    --no-dev \
    --no-interaction \
    --prefer-dist \
    --optimize-autoloader


FROM drupal:11.3-apache AS app

COPY certs/*.crt /usr/local/share/ca-certificates/

RUN update-ca-certificates

RUN apt-get update \
    && apt-get install -y --no-install-recommends \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libpng-dev \
        libwebp-dev \
        libavif-dev \
    && docker-php-ext-configure gd \
        --with-avif \
        --with-freetype \
        --with-jpeg \
        --with-webp \
    && docker-php-ext-install -j"$(nproc)" gd \
    && rm -rf /var/lib/apt/lists/*

WORKDIR /opt/openintranet

COPY --from=build /src/openintranet/ ./

RUN mkdir -p \
        web/sites/default/files \
        private \
    && chown -R www-data:www-data \
        web/sites/default/files \
        private

RUN printf '%s\n' \
    '<VirtualHost *:80>' \
    '    DocumentRoot /opt/openintranet/web' \
    '    <Directory /opt/openintranet/web>' \
    '        AllowOverride All' \
    '        Require all granted' \
    '    </Directory>' \
    '</VirtualHost>' \
    > /etc/apache2/sites-available/000-default.conf

RUN a2enmod rewrite

WORKDIR /opt/openintranet

CMD ["apache2-foreground"]