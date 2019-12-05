FROM ubuntu:latest
RUN mkdir -p /var/dev/craft/
RUN chmod -R 777 /var/dev/craft/
RUN apt-get update && apt-get upgrade -y
RUN ln -fs /usr/share/zoneinfo/America/Toronto /etc/localtime
RUN apt-get install php7.2 -y
RUN apt-get install php-pear php7.2-curl php7.2-dev php7.2-gd php7.2-mbstring php7.2-zip php7.2-mysql php7.2-xml -y
CMD ["php", "-S", "0.0.0.0:80", "-t", "/var/dev/craft/web/"]
