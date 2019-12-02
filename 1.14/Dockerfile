FROM ubuntu:18.04

ENV DEBIAN_FRONTEND noninteractive
ENV TERM xterm
ENV USER_UID 1000
ENV USER_NAME me
ENV USER_HOME /home/me

RUN echo "deb http://ppa.launchpad.net/vincent-c/wesnoth/ubuntu bionic main" > /etc/apt/sources.list.d/wesnoth.list
RUN useradd -ms /bin/bash -u $USER_UID $USER_NAME
RUN apt-get update && apt-get dist-upgrade -y && \
    apt-key adv --keyserver keyserver.ubuntu.com --recv-keys FE1FFCE65CB95493 && \
    apt install -y --no-install-recommends --allow-unauthenticated \
        wesnoth-1.14-core \
        wesnoth-1.14-tools \
        python3 \
        python3-enchant && \
    # CLEAN UP
    apt-get clean -y && \
    apt-get autoclean -y && \
    apt-get autoremove -y && \
    rm -rf /var/lib/log/* /tmp/* /var/tmp/*

COPY scripts/* /usr/local/bin/

USER me

WORKDIR ${USER_HOME}/.local/share/wesnoth/1.14/data/add-ons
