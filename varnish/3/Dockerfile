FROM debian:wheezy-backports

RUN apt-get update && DEBIAN_FRONTEND=noninteractive apt-get install -y varnish

COPY default.vcl /etc/varnish/default.vcl

COPY varnish-foreground /usr/local/bin/varnish-foreground
RUN chmod +x /usr/local/bin/varnish-foreground

EXPOSE 6081

CMD ["varnish-foreground"]

