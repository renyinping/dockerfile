# OpenWrt 14.07 Build System
FROM yinping/img:ubuntu-14.04

MAINTAINER yp_ren@hotmail.com

USER ubuntu

WORKDIR /home/ubuntu
RUN git clone https://git.openwrt.org/14.07/openwrt.git

WORKDIR /home/ubuntu/openwrt
RUN ./scripts/feeds update -a \
 && ./scripts/feeds install -a

CMD ["/usr/sbin/sshd","-D"]
