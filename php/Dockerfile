FROM php:7.4-fpm

RUN apt-get update && apt-get install -y zlib1g-dev g++ git libicu-dev zip libzip-dev zip \
    && docker-php-ext-install intl opcache pdo pdo_mysql \
    && pecl install apcu \
    && docker-php-ext-enable apcu \
    && docker-php-ext-configure zip \
    && docker-php-ext-install zip

#RUN apt-get -qq update \
#    && apt-get install libpng-dev --assume-yes \
#    && docker-php-ext-install pdo_mysql gd calendar opcache \
#    && pecl install xdebug-2.9.5 \
#    && docker-php-ext-enable xdebug \
#    && apt-get remove libpng-dev --assume-yes \
#	&& apt-get clean

WORKDIR /var/www/sf

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

RUN curl -sS https://get.symfony.com/cli/installer | bash
RUN mv /root/.symfony/bin/symfony /usr/local/bin/symfony