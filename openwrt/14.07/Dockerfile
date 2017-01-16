# OpenWrt 14.07 Build System

FROM yinping/img:ubuntu-14.04

USER ubuntu
 
RUN cd ${HOME} \
 && git clone https://git.openwrt.org/14.07/openwrt.git \
 && cd openwrt \
 && ./scripts/feeds update -a \
 && ./scripts/feeds install -a
