FROM docker.io/serversideup/php:8.3-fpm-nginx-alpine
WORKDIR /var/www/html

USER root
RUN apk update; \
  apk add --no-cache git;

USER www-data
RUN set -ex; \
  git clone https://github.com/laravel/laravel --depth=1 .; \
  rm -rf .git; \
  composer install;
RUN set -ex; \
  cp .env.example .env; \
  touch database/database.sqlite; \
  php artisan key:generate; \
  php artisan migrate;
