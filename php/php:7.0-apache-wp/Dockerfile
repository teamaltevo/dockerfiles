# writools/php:7.3-apache-craft-runtime
FROM php:7.0-apache as runtime
# ADD ./templates/php.ini /usr/local/etc/php/conf.d/app.ini

RUN apt-get update && \
    apt-get install -y --no-install-recommends \
    libicu-dev wget unzip curl zlib1g-dev 

# Install PDO_MySql
RUN docker-php-ext-install pdo_mysql 
RUN docker-php-ext-install mysqli


# Install zip extension
RUN apt-get install -y --no-install-recommends libzip-dev
RUN docker-php-ext-install zip

# Cleaning apt temp files
RUN apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*