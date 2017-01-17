# OpenWrt 14.07 Build System
FROM ubuntu:14.04

MAINTAINER yp_ren@hotmail.com

USER root

RUN apt-get update \
 && apt-get install -y \
        lib32z1 lib32ncurses5 lib32bz2-1.0 lib32stdc++6 \
        build-essential ccache \
        libncurses5-dev libssl-dev \
        git subversion mercurial \
        gawk vim unzip bash bash-completion \
        screen tmux wget sudo openssh-server \
 && apt-get autoremove \
 && apt-get clean

# 配置中文编码
RUN locale-gen zh_CN.UTF-8 en_US.UTF-8 \
 && echo 'LANG="zh_CN.UTF-8"'     >> /etc/environment \
 && echo 'LANGUAGE="en_US.UTF-8"' >> /etc/environment

# 添加用户ubuntu
RUN useradd -m -s /bin/bash ubuntu \
 && echo 'ubuntu:ubuntu' | chpasswd \
 && echo 'ubuntu ALL=NOPASSWD: ALL' > /etc/sudoers.d/ubuntu \
 && chmod 440 /etc/sudoers.d/ubuntu

# 配置ssh-server
RUN mkdir /var/run/sshd \
 && echo 'ClientAliveInterval 30' >> /etc/ssh/sshd_config \
 && echo 'ClientAliveCountMax 6'  >> /etc/ssh/sshd_config \
 && sed -i 's/^Port 22$/Port 2022/g' /etc/ssh/sshd_config

# OpenWrt Build System
USER ubuntu

WORKDIR /home/ubuntu
RUN git clone https://git.openwrt.org/14.07/openwrt.git

WORKDIR /home/ubuntu/openwrt
RUN ./scripts/feeds update -a \
 && ./scripts/feeds install -a

RUN wget https://github.com/renyinping/wndr3700v4/raw/openwrt/nand128m.sh \
 && /bin/bash nand128m.sh \
 && wget https://github.com/renyinping/wndr3700v4/raw/openwrt/nfs-kernel-server.not-kmod \
 && /bin/bash nfs-kernel-server.not-kmod \
 && wget https://github.com/renyinping/wndr3700v4/raw/openwrt/config.tar.gz \
 && tar -zxvf config.tar.gz
 
RUN make download

CMD ["sudo","/usr/sbin/sshd","-D"]
