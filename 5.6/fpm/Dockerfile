FROM php:5.6-fpm
MAINTAINER David GUENAULT

RUN     apt-get -y update && \
        apt-get -y install git libcurl4-gnutls-dev libmcrypt-dev libpng12-dev libxml2-dev libxslt-dev vim-nox mysql-client ssmtp && \
        apt-get install -y libfreetype6-dev libjpeg62-turbo-dev libpng12-dev libghc-text-icu-dev bsd-mailx && \
        docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ && \
        docker-php-ext-install -j$(nproc) curl bcmath gd mcrypt mysql mysqli opcache pdo_mysql soap xsl zip iconv gd intl mbstring && \
        apt-get -y clean && \
        apt-get -y autoremove && \
        rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*
