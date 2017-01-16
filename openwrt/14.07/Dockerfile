# OpenWrt 14.07 Build System
FROM yinping/img:ubuntu-14.04

MAINTAINER yp_ren@hotmail.com

USER ubuntu
WORKDIR ${HOME}
RUN git clone https://git.openwrt.org/14.07/openwrt.git \
 && cd openwrt \
 && ./scripts/feeds update -a \
 && ./scripts/feeds install -a
