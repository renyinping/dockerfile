# OpenWrt 14.07 Build System

FROM ubuntu:14.04

RUN apt-get update \
 && apt-get install -y \
        lib32z1 lib32ncurses5 lib32bz2-1.0 lib32stdc++6 \
        build-essential ccache \
        libncurses5-dev libssl-dev \
        git subversion mercurial \
        unzip gawk wget \
        locales sudo bash bash-completion vim \
 && apt-get autoremove \
 && apt-get clean \
    \
 && locale-gen zh_CN.UTF-8 en_US.UTF-8 \
 && echo 'LANG="zh_CN.UTF-8"'     >> /etc/environment \
 && echo 'LANGUAGE="en_US.UTF-8"' >> /etc/environment \
    \
 && useradd -m -s /bin/bash ubuntu \
 && echo 'ubuntu:ubuntu' | chpasswd \
 && echo 'ubuntu ALL=NOPASSWD: ALL' > /etc/sudoers.d/ubuntu \
 && chmod 440 /etc/sudoers.d/ubuntu
 
RUN git clone https://git.openwrt.org/14.07/openwrt.git \
 && cd openwrt \
 && ./scripts/feeds update -a \
 && ./scripts/feeds install -a
