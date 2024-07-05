FROM php:8.3-fpm

RUN apt update && apt install -y unzip zip

COPY --from=composer /usr/bin/composer /usr/bin/composer

RUN apt update
RUN apt install -y vim libpq-dev libpng-dev libjpeg-dev libfreetype-dev libtidy-dev zip unzip libzip-dev libxslt-dev \
    && docker-php-ext-configure gd --with-freetype --with-jpeg \
    && docker-php-ext-install pdo_pgsql intl gd zip tidy xsl \
    && docker-php-ext-enable tidy zip xsl

RUN cp "$PHP_INI_DIR/php.ini-development" "$PHP_INI_DIR/php.ini"
RUN cp "$PHP_INI_DIR/php.ini-production" "$PHP_INI_DIR/php.ini"
