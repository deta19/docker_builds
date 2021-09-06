FROM ubuntu:18.04

ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update && apt-get upgrade && apt-get install -y apt-utils \
    software-properties-common \
    ca-certificates apt-transport-https

RUN add-apt-repository -y ppa:ondrej/php

RUN apt-get update && apt-get install -y \
    curl \
    # Install apache
    apache2 \
    # Install php 7.3
    libapache2-mod-php7.3 \
    php7.3 \
    php7.3-cli \
    php7.3-common \
    php7.3-curl \
    php7.3-mbstring \
    php7.3-mysql \
    php7.3-xml \
    php7.3-zip \
    php7.3-Intl \
    php7.3-mysqli \
    php7.3-json \
    php7.3-fpm \
    php7.3-gd \
    php7.3-ldap \
    php7.3-soap \
    php-imagick \
    # Install tools
    nano \
    imagemagick \
    ca-certificates \
    && apt clean

# Install composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

 EXPOSE 80 443

WORKDIR /var/www

HEALTHCHECK --interval=5s --timeout=3s --retries=3 CMD curl -f http://localhost || exit 1

CMD apachectl -D FOREGROUND 