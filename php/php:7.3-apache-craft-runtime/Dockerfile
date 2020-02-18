# writools/php:7.3-apache-craft-runtime
FROM php:7.3-apache as runtime
ADD ./templates/php.ini /usr/local/etc/php/conf.d/app.ini
ADD ./templates/vhost.conf /etc/apache2/sites-available/000-default.conf
ADD ./templates/apache.conf /etc/apache2/conf-available/app.conf
RUN a2enconf app
RUN a2enmod rewrite remoteip

RUN apt-get update && \
    apt-get install -y --no-install-recommends \
    libicu-dev wget unzip curl zlib1g-dev 

# Install PDO_MySql
RUN docker-php-ext-install pdo_mysql 

# Install zip extension
RUN apt-get install -y --no-install-recommends libzip-dev
RUN docker-php-ext-install zip

# Install imagemagick
RUN apt-get update && apt-get install -y libmagickwand-dev --no-install-recommends && rm -rf /var/lib/apt/lists/*
RUN pecl install imagick
RUN docker-php-ext-enable imagick

# Cleaning apt temp files
RUN apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*