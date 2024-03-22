FROM ubuntu:22.04

ENV TERM xterm
ENV USER_UID 1000
ENV USER_NAME me
ENV USER_HOME /home/me

RUN useradd -ms /bin/bash -u $USER_UID $USER_NAME && \
    apt-get update && apt-get dist-upgrade -y && \
    apt-get install -y software-properties-common && \
    add-apt-repository ppa:xtradeb/play && \
    apt update && \
    apt-get install -y --no-install-recommends --allow-unauthenticated \
        wesnoth-core \
        wesnoth-tools \
        python3 \
        python3-enchant && \
    ln -s /usr/share/games/wesnoth/data/tools/wmllint /usr/local/bin/wmllint && \  
    ln -s /usr/share/games/wesnoth/data/tools/wmlindent /usr/local/bin/wmlindent && \    
    ln -s /usr/share/games/wesnoth/data/tools/wmlxgettext /usr/local/bin/wmlxgettext && \
    # CLEAN UP
    apt-get clean -y && \
    apt-get autoclean -y && \
    apt-get autoremove -y && \
    rm -rf /var/lib/log/* /tmp/* /var/tmp/*

COPY scripts/* /usr/local/bin/

USER me

WORKDIR ${USER_HOME}/.local/share/wesnoth/1.18/data/add-ons
