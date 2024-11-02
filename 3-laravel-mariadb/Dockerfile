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

COPY --chmod=755 ./entrypoint.d/ /etc/entrypoint.d/
