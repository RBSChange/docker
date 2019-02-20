FROM jlesage/baseimage-gui:ubuntu-18.04

RUN apt-get update && apt-get update && apt-get install -y wget libasound2 libasound2-plugins libdbus-glib-1-2 libgtk2.0-0 unzip \
    && mkdir /firefox \
    && wget https://ftp.mozilla.org/pub/firefox/releases/24.0esr/linux-x86_64/fr/firefox-24.0esr.tar.bz2 -O /tmp/firefox.tbz2 \
    && tar -jxf /tmp/firefox.tbz2 -C /firefox/ --strip-components=1

ENV APP_NAME="FirefoxESR24"

COPY rootfs/ /

COPY rbs-change-manager-1.40.1.xpi /rbs-change-manager.xpi

