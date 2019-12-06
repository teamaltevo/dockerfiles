FROM ubuntu:latest
RUN mkdir -p /var/dev/craft/
RUN chmod -R 777 /var/dev/craft/
RUN apt-get update && apt-get upgrade -y
RUN ln -fs /usr/share/zoneinfo/America/Toronto /etc/localtime

# Install php and extensions
RUN apt-get install php7.2 -y
RUN apt-get install php-pear php7.2-curl php7.2-dev php7.2-gd php7.2-mbstring php7.2-zip php7.2-mysql php7.2-xml wget unzip curl -y

# Install composer
RUN curl -sS https://getcomposer.org/installer |php
RUN mv composer.phar /usr/local/bin/composer

# Install node and NPM
RUN curl -sL https://deb.nodesource.com/setup_12.x | bash -
RUN apt install nodejs -y

CMD ["php", "-S", "0.0.0.0:80", "-t", "/var/dev/craft/web/"]
