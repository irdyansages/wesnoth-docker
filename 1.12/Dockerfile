FROM ubuntu:16.04

MAINTAINER Jakub Konečný <jakub.konecny2@centrum.cz>

ENV TERM xterm
ENV USER_UID 1000
ENV USER_NAME me
ENV USER_HOME /home/me

RUN echo "deb http://ppa.launchpad.net/vincent-c/wesnoth/ubuntu xenial main" > /etc/apt/sources.list.d/wesnoth.list
RUN useradd -ms /bin/bash -u $USER_UID $USER_NAME
RUN apt-get update && apt-get dist-upgrade -y && \
    apt install -y --no-install-recommends --allow-unauthenticated \
        wesnoth-1.12-core \
        wesnoth-1.12-tools \
        python-enchant
RUN apt-get clean -y
RUN apt-get autoclean -y
RUN apt-get autoremove -y
RUN rm -rf /var/lib/log/* /tmp/* /var/tmp/*

COPY scripts/* /usr/local/bin/

USER me

WORKDIR ${USER_HOME}/.local/share/wesnoth/1.12/data/add-ons
