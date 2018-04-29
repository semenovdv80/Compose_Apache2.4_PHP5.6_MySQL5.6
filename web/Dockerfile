FROM php:5.6-apache
# Workaround for permission to volumes
#RUN usermod -u 1000 www-data
#RUN groupmod -g 33 www-data
# Enable Apache mod_rewrite
RUN a2enmod rewrite

ENV APACHE_RUN_USER www-data
ENV APACHE_RUN_GROUP www-data
ENV APACHE_LOG_DIR /var/log/apache2
ENV APACHE_LOCK_DIR /var/lock/apache2
ENV APACHE_PID_FILE /var/run/apache2.pid

# Install packages
RUN apt-get update
RUN apt-get install -y libpng-dev libc-client-dev libkrb5-dev
RUN apt-get install -y libmcrypt-dev
RUN apt-get install nano
RUN docker-php-ext-configure imap --with-kerberos --with-imap-ssl
RUN docker-php-ext-install imap
RUN docker-php-ext-install pdo_mysql mysqli gd
RUN docker-php-ext-install mysql