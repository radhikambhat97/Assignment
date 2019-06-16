FROM ubuntu:latest
MAINTAINER Dan Pupius <dan@pupi.us>

# Install apache, PHP, and supplimentary programs. openssh-server, curl, and lynx-cur are for debugging the container.
RUN apt-get update && apt-get -y upgrade
ENV DEBIAN_FRONTEND=noninteractive 

RUN apt-get -y install apache2
RUN apt-get -y install php php-mysql
RUN a2enmod rewrite
#RUN apt-get install php7.0 libapache2-mod-php7.0
RUN echo "ServerName localhost" >> /etc/apache2/apache2.conf

# Enable apache mods.
#RUN a2enmod php
#RUN a2enmod rewrite

# Update the PHP.ini file, enable <? ?> tags and quieten logging.
#RUN sed -i "s/short_open_tag = Off/short_open_tag = On/" /etc/php/7.0/apache2/php.ini
#RUN sed -i "s/error_reporting = .*$/error_reporting = E_ERROR | E_WARNING | E_PARSE/" /etc/php/7.0/apache2/php.ini

# Manually set up the apache environment variables
#ENV APACHE_RUN_USER www-data
#ENV APACHE_RUN_GROUP www-data
#ENV APACHE_LOG_DIR /var/log/apache2
#ENV APACHE_LOCK_DIR /var/lock/apache2
#ENV APACHE_PID_FILE /var/run/apache2.pid
RUN rm -rf /etc/apache2/sites-available/000-default.conf
# Expose apache.
EXPOSE 80
COPY 000-default.conf /etc/apache2/sites-available/000-default.conf
# Copy this repo into place.
COPY index.html /var/www/html/index.html
CMD echo "ServerName localhost" >> /etc/apache2/apache2.conf
# Update the default apache site with the config we created.
#ADD apache-config.conf /etc/apache2/sites-enabled/000-default.conf

# By default start up apache in the foreground, override with /bin/bash for interative.
CMD /usr/sbin/apache2ctl -D FOREGROUND

