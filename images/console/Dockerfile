  FROM php:7.2
  MAINTAINER zyd <3957@qq.com>

  RUN apt-get update && apt-get install -y git curl  libpng-dev libjpeg-dev libzip-dev libfreetype6-dev unzip\
    && rm -rf /var/lib/apt/lists/* \
    && pecl install zip \
    && docker-php-ext-enable zip \
    && docker-php-ext-configure gd --with-png-dir=/usr --with-jpeg-dir=/usr --with-freetype-dir=/usr  \
    && docker-php-ext-install gd mysqli pdo_mysql opcache

  RUN git config --global user.name "3957" \
    && git config --global user.email "117663444@qq.com"

# 安装与配置 composer
# Composer 官方安装脚本 https://getcomposer.org/download/
# 因为在国内下载 composer 太慢，我们直接把下载下来的 composer 复制到容器里使用。
COPY ./composer.phar /usr/local/bin/composer
RUN chmod +x /usr/local/bin/composer
RUN echo 'export PATH="$PATH:$HOME/.composer/vendor/bin"' >> ~/.bashrc \
  && . ~/.bashrc \
#  && useradd www-deploy -g www-data \
#  && su www-deploy \
  && composer config -g repo.packagist composer https://packagist.laravel-china.org
