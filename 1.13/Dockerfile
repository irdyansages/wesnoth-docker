FROM ubuntu:16.04

MAINTAINER Jakub Konečný <jakub.konecny2@centrum.cz>

ENV TERM xterm
ENV USER_UID 1000
ENV USER_NAME me
ENV USER_HOME /home/me

RUN echo "deb http://ppa.launchpad.net/pkg-games/wesnoth-devel/ubuntu xenial main" > /etc/apt/sources.list.d/php.list
RUN apt-get update && apt-get dist-upgrade -y
RUN useradd -ms /bin/bash -u $USER_UID $USER_NAME
RUN apt install -y --no-install-recommends --allow-unauthenticated \
        wesnoth-1.13-core \
        wesnoth-1.13-tools \
        python3 \
        python3-enchant
RUN apt-get clean -y
RUN apt-get autoclean -y
RUN apt-get autoremove -y
RUN rm -rf /var/lib/log/* /tmp/* /var/tmp/*

ADD download_addon /usr/local/bin/

WORKDIR ${USER_HOME}/.local/share/wesnoth/1.13/data/add-ons
