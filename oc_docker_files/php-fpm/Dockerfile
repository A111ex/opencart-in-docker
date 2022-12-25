# php-fpm 
FROM php:7.4.14-fpm
RUN apt-get update && apt-get install -y \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libmcrypt-dev \
        libpng-dev \
        libzip-dev
RUN docker-php-ext-install -j$(nproc) iconv  \
        && docker-php-ext-configure gd --with-freetype --with-jpeg \
        && docker-php-ext-install -j$(nproc) gd

#xdebug
RUN pecl install xdebug-2.8.1 && docker-php-ext-enable xdebug

RUN docker-php-ext-install -j$(nproc) mysqli
RUN docker-php-ext-install -j$(nproc) zip

COPY xdebug.ini /usr/local/etc/php/conf.d/xdebug.ini

CMD ["php-fpm"]  
EXPOSE 9000

