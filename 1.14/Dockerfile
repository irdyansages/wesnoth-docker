FROM ubuntu:16.04

ENV TERM xterm
ENV USER_UID 1000
ENV USER_NAME me
ENV USER_HOME /home/me

RUN echo "deb http://ppa.launchpad.net/vincent-c/wesnoth/ubuntu xenial main" > /etc/apt/sources.list.d/wesnoth.list
RUN useradd -ms /bin/bash -u $USER_UID $USER_NAME
RUN apt-get update && apt-get dist-upgrade -y && \
    apt install -y --no-install-recommends --allow-unauthenticated \
        wesnoth-1.14-core \
        wesnoth-1.14-tools \
        python3 \
        python3-enchant && \
    ln -s /usr/share/games/wesnoth/1.14/data/tools/wmllint /usr/local/bin/wmllint && \  
    ln -s /usr/share/games/wesnoth/1.14/data/tools/wmlindent /usr/local/bin/wmlindent && \    
    ln -s /usr/share/games/wesnoth/1.14/data/tools/wmlxgettext /usr/local/bin/wmlxgettext && \
    # CLEAN UP
    apt-get clean -y && \
    apt-get autoclean -y && \
    apt-get autoremove -y && \
    rm -rf /var/lib/log/* /tmp/* /var/tmp/*

COPY scripts/* /usr/local/bin/

USER me

WORKDIR ${USER_HOME}/.local/share/wesnoth/1.14/data/add-ons
