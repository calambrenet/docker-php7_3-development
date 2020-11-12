
FROM php:7.3.23-apache
RUN apt-get update && apt-get install -y \
    zlib1g-dev \
    libzip-dev \
    git

RUN docker-php-ext-install pdo pdo_mysql mysqli zip

RUN mkdir /src && cd /src && git clone https://github.com/xdebug/xdebug.git \
    && cd xdebug \
    && sh ./rebuild.sh \
    && docker-php-source extract \
    && docker-php-ext-enable xdebug\
    && docker-php-source delete \
    && cd  / && rm -fr /src

RUN a2enmod rewrite
