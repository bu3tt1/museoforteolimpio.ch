FROM php:7.2-apache

# configure PHP
RUN set -ex; \
    \
    apt-get update; \
    \
    # opcache
    docker-php-ext-install opcache; \
    # gd
    apt-get install -y libfreetype6-dev libjpeg62-turbo-dev libpng-dev; \
    docker-php-ext-install -j$(nproc) iconv; \
    docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ ; \
    docker-php-ext-install -j$(nproc) gd ; \
    # zip
    apt-get install -y libzip-dev; \
    docker-php-ext-install zip; \
    # mod_rewrite extension
    a2enmod rewrite

# install Grav
RUN set -ex; \
    \
    apt-get install unzip; \
    \
    cd /var/www/html; \
	\
    curl -o grav.zip -fSL "https://getgrav.org/download/core/grav-admin/1.6.11"; \
    unzip grav.zip; \
    rm -rf grav.zip; \
    mv grav-admin/* ./; \
    \
    rm -rf user/*; \
    \
    cp webserver-configs/htaccess.txt ./.htaccess; \
    \
    chown -R www-data:www-data ./

