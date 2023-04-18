FROM php:8.1-fpm

ENV TZ="America/Sao_Paulo"

RUN apt-get update && apt-get install -y \
    libzip-dev \
    zip \
    git \
    vim \
    && docker-php-ext-install mysqli \
    && docker-php-ext-install pdo_mysql \
    && docker-php-ext-install opcache \
    && docker-php-ext-configure zip \
    && docker-php-ext-install zip \
    && docker-php-ext-configure opcache --enable-opcache \
    && docker-php-ext-install opcache

# COMPOSER
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer
RUN composer --version

### XDEBUG ###
RUN echo "Start install Xdebug" \
    && git clone https://github.com/xdebug/xdebug.git \
    && cd xdebug \
    && phpize \
    && ./configure --enable-xdebug \
    && make \
    && make install \
    && echo "End install Xdebug"
