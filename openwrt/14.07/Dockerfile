# OpenWrt 14.07 Build System

FROM ubuntu:14.04

RUN apt-get update \
 && apt-get install -y \
        lib32z1 lib32ncurses5 lib32bz2-1.0 lib32stdc++6 \
        build-essential ccache \
        libncurses5-dev libssl-dev \
        git subversion mercurial \
        unzip gawk screen tmux \
 && apt-get autoremove \
 && apt-get clean
 
RUN git clone https://git.openwrt.org/14.07/openwrt.git \
 && cd openwrt \
 && ./scripts/feeds update -a \
 && ./scripts/feeds install -a
