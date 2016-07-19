FROM ubuntu:latest
MAINTAINER Matt Johnson <mjohnson@handlpartners.com>

# Setup Environment
ENV DEBIAN_FRONTEND noninteractive

# Update Sources
RUN apt-get update -y

# Install Apache
RUN apt-get install -y apache2
RUN mkdir -p /var/lock/apache2 /var/run/apache2
RUN rm -rf /var/www/html && mkdir /var/www/html
RUN a2enmod rewrite

# Install MySQL and bind to 0.0.0.0 for SequelPro
RUN apt-get install -y mysql-client mysql-server
RUN sed -i -e"s/^bind-address\s*=\s*127.0.0.1/bind-address = 0.0.0.0/" /etc/mysql/mysql.conf.d/mysqld.cnf

# Install PHP 5.6
RUN apt-get install -y software-properties-common python-software-properties
RUN add-apt-repository ppa:ondrej/php
RUN apt-key update
RUN apt-get update
RUN apt-get install -y --allow-unauthenticated php5.6 php5.6-common php5.6-cli php5.6-curl php5.6-gd php5.6-mysql php5.6-opcache php5.6-json php5.6-mcrypt php5.6-mbstring php5.6-xml

# Install Supervisor
RUN apt-get install -y supervisor
RUN mkdir -p /var/log/supervisor

# Add volumes and configs
ADD supervisord.conf /etc/

# Expose ports and set launch script
EXPOSE 80 3306
CMD ["/usr/bin/supervisord"]
