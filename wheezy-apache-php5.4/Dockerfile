FROM debian:wheezy-backports

RUN apt-get update && DEBIAN_FRONTEND=noninteractive apt-get install -y supervisor \
    cron vim ca-certificates curl netcat sudo git unzip python-pip inetutils-ping man wget ssmtp sudo \
    apache2 php5 \
    libapache2-mod-php5 php-pear php5-common php5-curl php5-gd php5-imagick php5-intl \
    php5-mcrypt php5-memcache php5-mysql php5-xdebug php5-xsl php5-ldap \
    php-net-smtp php-apc php-auth-sasl php-http-request php-mail php-mail-mime php-mail-mimedecode \
    php-net-dime php-net-smtp php-net-socket php-net-url php-pear php-soap

COPY apache2-foreground /usr/local/bin/apache2-foreground
COPY apache2-vhost.conf /etc/apache2/sites-enabled/000-default

RUN useradd -g www-data -G sudo -s /bin/bash -m -d /home/docker docker \
    && a2enmod rewrite headers php5 \
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

WORKDIR /var/www/rbschange

EXPOSE 8080

CMD ["apache2-foreground"]

