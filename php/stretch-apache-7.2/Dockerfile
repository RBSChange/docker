FROM debian:stretch-backports

RUN apt-get update && DEBIAN_FRONTEND=noninteractive apt-get install -y supervisor \
    cron vim apt-transport-https ca-certificates curl netcat git unzip python-pip inetutils-ping man wget sudo gnupg

RUN wget -q https://packages.sury.org/php/apt.gpg -O- | apt-key add - && echo "deb https://packages.sury.org/php/ stretch main" | tee /etc/apt/sources.list.d/php.list

RUN apt-get update && DEBIAN_FRONTEND=noninteractive apt-get install -y apache2 php7.2 \
        libapache2-mod-php7.2 php-pear php7.2-curl php7.2-gd php-imagick php7.2-intl php7.2-mbstring \
        php-memcache php7.2-mysql php-xdebug php7.2-xsl php7.2-ldap php7.2-zip \
        php-net-smtp php-auth-sasl php-http-request php-mail php-mail-mime \
        php-net-dime php-net-smtp php-net-socket php-net-url php-pear php-soap

COPY apache2-foreground /usr/local/bin/apache2-foreground
COPY apache2-vhost.conf /etc/apache2/sites-available/000-default.conf

RUN useradd -g www-data -G sudo -s /bin/bash -m -d /home/docker docker \
    && a2enmod rewrite headers php7.2 \
    && chmod +x /usr/local/bin/apache2-foreground \
    && sed -i 's/export APACHE_RUN_USER=.*/export APACHE_RUN_USER=docker/' /etc/apache2/envvars \
    && sed -i -r 's/APACHE_PID_FILE=.*$/APACHE_PID_FILE=\/var\/run\/apache2\/apache2$SUFFIX.pid/g' /etc/apache2/envvars \
    && sed -i -r 's/([^0-9])80$/\18080/g' /etc/apache2/ports.conf \
    && mkdir /var/www/rbschange \
    && chown -R docker /var/run/apache2 /var/lock/apache2 /var/log/apache2 /var/www \
    && set -ex \
    && . "/etc/apache2/envvars" > /dev/null 2>&1 \
    && ln -sfT /dev/stderr "$APACHE_LOG_DIR/error.log" \
    && ln -sfT /dev/stdout "$APACHE_LOG_DIR/access.log" \
    && ln -sfT /dev/stdout "$APACHE_LOG_DIR/other_vhosts_access.log"

RUN wget -q https://getcomposer.org/download/1.6.5/composer.phar -O /usr/local/bin/composer \
    && chmod +x /usr/local/bin/composer

COPY 99-custom.ini /etc/php/7.2/apache2/conf.d/99-custom.ini

WORKDIR /var/www/rbschange

USER docker

EXPOSE 8080

CMD ["apache2-foreground"]
