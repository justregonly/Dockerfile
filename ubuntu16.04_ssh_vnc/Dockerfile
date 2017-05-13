FROM ubuntu:16.04
MAINTAINER Mysci
ENV DEBIAN_FRONTEND noninteractive
ENV USER root
RUN apt-get update && \
    apt-get install -y --no-install-recommends ubuntu-desktop && \
    apt-get install -y gnome-panel gnome-settings-daemon metacity nautilus gnome-terminal openssh-server && \
    apt-get install -y tightvncserver && \
    mkdir /root/.vnc && \
    mkdir -p /var/run/sshd && \
    echo 'root:root' | chpasswd && \
    sed -ri 's/^PermitRootLogin\s+.*/PermitRootLogin yes/' /etc/ssh/sshd_config && \
    sed -ri 's/UsePAM yes/#UsePAM yes/g' /etc/ssh/sshd_config
ENV DEBIAN_FRONTEND newt
ADD xstartup /root/.vnc/xstartup

EXPOSE 22 80 443 9001 9091 
CMD    ["/usr/sbin/sshd", "-D"]

