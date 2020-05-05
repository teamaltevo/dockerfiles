# writools/php:7.3-apache-craft-runtime
FROM php:7.0-apache as runtime
# ADD ./templates/php.ini /usr/local/etc/php/conf.d/app.ini
COPY ./templates/vhost-config.conf /etc/apache2/sites-available/000-default.conf
RUN a2enmod rewrite 

RUN apt-get update && \
    apt-get install -y --no-install-recommends \
    libicu-dev wget unzip curl zlib1g-dev 

# Install PDO_MySql
RUN docker-php-ext-install pdo_mysql 
RUN docker-php-ext-install mysqli

# Install zip extension
RUN apt-get install -y --no-install-recommends libzip-dev
RUN docker-php-ext-install zip

# Install WP-CLI
RUN apt-get update && apt-get install less
WORKDIR /opt
RUN curl -O https://raw.githubusercontent.com/wp-cli/builds/gh-pages/phar/wp-cli.phar
RUN chmod +x wp-cli.phar
RUN mv wp-cli.phar /usr/local/bin/wp

# Cleaning apt temp files
RUN apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*
WORKDIR /var/www/html