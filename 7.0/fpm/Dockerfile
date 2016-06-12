FROM php:7-fpm
MAINTAINER Siddhy NDiaye

ENV     DEBIAN_FRONTEND noninteractive


RUN     apt-get -y update && \
        apt-get -y install git libcurl4-gnutls-dev libmcrypt-dev libpng12-dev libxml2-dev libxslt-dev vim-nox mysql-client ssmtp && \
        apt-get install -y libfreetype6-dev libjpeg62-turbo-dev libpng12-dev libghc-text-icu-dev bsd-mailx && \
        apt-get -y install ssmtp bsd-mailx locales && \
        echo "fr_FR.UTF-8 UTF-8" >> /etc/locale.gen && \
        locale-gen fr_FR.UTF-8 && \
        /usr/sbin/update-locale LANG=fr_FR.UTF-8 && \
        docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ && \
        docker-php-ext-install -j$(nproc) curl bcmath gd mcrypt mysql mysqli opcache pdo_mysql soap xsl zip iconv gd intl mbstring xmlwriter && \
        apt-get -y clean && \
        apt-get -y autoremove && \
        rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

COPY    ssmtp.conf /etc/ssmtp/ssmtp.conf
COPY    revaliases /etc/ssmtp/revaliases
