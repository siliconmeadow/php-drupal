# Dockerfile inspired by "official" drupal docker images 
# (@see https://hub.docker.com/_/drupal/)
# 
# from https://www.drupal.org/requirements/php#drupalversions
FROM php:5.5-apache

RUN a2enmod rewrite

# install the PHP extensions we need
RUN apt-get update && apt-get install -y libpng12-dev libjpeg-dev libpq-dev mysql-client openssh-client vim-tiny git \
  && rm -rf /var/lib/apt/lists/* \
  && docker-php-ext-configure gd --with-png-dir=/usr --with-jpeg-dir=/usr \
  && docker-php-ext-install gd mbstring pdo pdo_mysql 

RUN apt-get update && apt-get install -y libmemcached-dev \
    && pecl install memcached \
    && docker-php-ext-enable memcached
    
COPY php.ini /usr/local/etc/php/
