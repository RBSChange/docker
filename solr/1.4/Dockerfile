FROM debian:wheezy-backports

RUN apt-get update && DEBIAN_FRONTEND=noninteractive apt-get install -y openjdk-7-jre-headless wget

RUN useradd -g users -s /bin/bash -d /usr/local/solr solr \
    && wget -q https://s3-eu-west-1.amazonaws.com/clickandmortar-shared/misc/solr-1.4.1.tgz -O /tmp/solr.tgz \
    && tar -zxf /tmp/solr.tgz -C /usr/local/ \
    && chown -R solr /usr/local/solr \
    && rm -f /tmp/solr.tgz

VOLUME ["/usr/local/solr/data"]

EXPOSE 8983

CMD ["/usr/local/solr/solr.sh"]

