# Gebruik een Ubuntu 22.04-image als basis
FROM ubuntu:22.04

# Bijwerken van het pakketbeheersysteem en installeren van Apache en PHP 8.1
RUN apt-get update && \
    DEBIAN_FRONTEND=noninteractive apt-get install -y apache2 php8.1 libapache2-mod-php8.1 && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

# Installeer de benodigde PHP-extensies voor MySQL-connectiviteit (PDO en PDO MySQL)
RUN apt-get update && \
    DEBIAN_FRONTEND=noninteractive apt-get install -y software-properties-common && \
    add-apt-repository ppa:ondrej/php && \
    apt-get update && \
    DEBIAN_FRONTEND=noninteractive apt-get install -y php8.1-pdo php8.1-mysql

# Configureer Apache voor PHP
RUN a2enmod php8.1
RUN echo "ServerName localhost" >> /etc/apache2/apache2.conf

# Stel de werkmappen in voor Apache-webinhoud
WORKDIR /var/www/html

# Start Apache bij het uitvoeren van de container
CMD ["/usr/sbin/apache2ctl", "-D", "FOREGROUND"]
