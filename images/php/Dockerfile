FROM php:7.2-fpm
MAINTAINER zyd <3957@qq.com>

RUN apt-get update && apt-get install -y libpng-dev libjpeg-dev libfreetype6-dev \
  && rm -rf /var/lib/apt/lists/* \
  && docker-php-ext-configure gd --with-png-dir=/usr --with-jpeg-dir=/usr --with-freetype-dir=/usr  \
  && docker-php-ext-install gd mysqli pdo_mysql opcache

RUN pecl install xdebug && docker-php-ext-enable xdebug
  
COPY ./config/php.ini /usr/local/etc/php/conf.d/
COPY ./config/opcache-recommended.ini /usr/local/etc/php/conf.d/
COPY ./config/xdebug_remote.log /var/log/

RUN chmod -R 777 /var/log/xdebug_remote.log