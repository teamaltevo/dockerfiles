FROM ubuntu:latest
RUN mkdir -p /var/dev/craft/
RUN chmod -R 777 /var/dev/craft/
RUN apt-get update && apt-get upgrade -y
RUN ln -fs /usr/share/zoneinfo/America/Toronto /etc/localtime

# Install php and extensions
RUN apt-get install software-properties-common -y
RUN add-apt-repository ppa:ondrej/php -y
RUN apt-get install php7.4 -y
RUN apt-get install php-pear php7.4-curl php7.4-dev php7.4-gd php7.4-mbstring php7.4-zip php7.4-mysql php7.4-xml php7.4-bcmath php7.4-intl wget unzip curl -y
COPY ./templates/php.ini /etc/php/7.4/cli/php.ini

# Install composer
RUN curl -sS https://getcomposer.org/installer |php
RUN mv composer.phar /usr/local/bin/composer

# Install node and NPM
RUN curl -fsSL https://deb.nodesource.com/setup_20.x | bash -
RUN apt-get install -y nodejs

CMD ["php", "-S", "0.0.0.0:80", "-t", "/var/dev/craft/web/"]
