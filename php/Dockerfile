FROM php:5.6-apache
MAINTAINER astrsk-hori <horie@astrsk.jp>
#COPY php.ini /usr/local/etc/php/
RUN apt-get update \
  && apt-get install -y libfreetype6-dev libjpeg62-turbo-dev libpng12-dev libmcrypt-dev git mysql-client vim zsh wget zip \
  && docker-php-ext-install pdo_mysql mysqli mbstring gd iconv mcrypt
RUN /usr/bin/curl -sS https://getcomposer.org/installer |php
RUN /bin/mv composer.phar /usr/local/bin/composer
COPY apache2.conf /etc/apache2/apache2.conf
