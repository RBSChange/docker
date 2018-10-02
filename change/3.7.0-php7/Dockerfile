FROM rbschange/php:7

RUN wget -q https://clickandmortar-shared.s3.amazonaws.com/clients/rbschange/cmsecomos-3.6.9-docker.tgz -O /tmp/change-docker.tgz \
    && tar -zxf /tmp/change-docker.tgz -C /var/www/rbschange --strip-components=1 \
    && chown -R docker:www-data /var/www/rbschange \
    && rm -f /tmp/change-docker.tgz
