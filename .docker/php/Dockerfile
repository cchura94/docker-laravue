#PHP
FROM php:8.2-fpm-alpine

RUN apt-get update \
    && apt-get install -y build-essential zlib1g-dev default-mysql-client curl pnupg procps vim git unzip libzip-dev libpq-dev \
    && docker-php-ext-install zip pdo_mysql pdo_pgsql pgsql

RUN apt-get install -y libicu-dev \
    && docker-php-ext-configure intl \
    && docker-php-ext-install intl

# composer
RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
RUN -r "if (hash_file('sha384', 'composer-setup.php') === 'dac665fdc30fdd8ec78b38b9800061b4150413ff2e3b6f88543c636f7cd84f6db9189d43a81e5503cda447da73c7e5b6') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"
RUN php composer-setup.php
RUN -r "unlink('composer-setup.php');"

RUN mv composer.phar /usr/local/bin/composer


WORKDIR /var/www
