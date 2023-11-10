FROM php:8.2-fpm-alpine

ADD https://github.com/mlocati/docker-php-extension-installer/releases/latest/download/install-php-extensions /usr/local/bin/

RUN chmod +x /usr/local/bin/install-php-extensions && \
    install-php-extensions xdebug && apk add php-xsl && apk add php-dom

RUN mv "$PHP_INI_DIR/php.ini-development" "$PHP_INI_DIR/php.ini"
COPY php.ini "$PHP_INI_DIR/conf.d/php.ini"
COPY xdebug.ini "$PHP_INI_DIR/conf.d/xdebug.ini"
COPY --from=composer /usr/bin/composer /usr/bin/composer