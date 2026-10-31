# PHPはパッチ番号まで固定する（2026-10-21 公開のセキュリティ修正版）
FROM php:8.5.12-fpm

RUN apt-get update \
    && apt-get install -y --no-install-recommends git unzip libpq-dev libzip-dev \
    && docker-php-ext-install pdo_pgsql zip \
    && rm -rf /var/lib/apt/lists/*

COPY --from=composer:2 /usr/bin/composer /usr/bin/composer

WORKDIR /var/www/html
