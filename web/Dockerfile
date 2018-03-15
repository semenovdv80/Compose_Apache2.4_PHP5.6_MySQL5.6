FROM php:5.6-apache
# Workaround for permission to volumes
RUN usermod -u 1000 www-data
RUN groupmod -g 33 www-data
# Enable Apache mod_rewrite
RUN a2enmod rewrite
# Install packages
RUN apt-get update
RUN apt-get install -y libpng-dev libc-client-dev libkrb5-dev
RUN apt-get install -y libmcrypt-dev
RUN docker-php-ext-configure imap --with-kerberos --with-imap-ssl
RUN docker-php-ext-install imap
RUN docker-php-ext-install pdo_mysql mysqli gd