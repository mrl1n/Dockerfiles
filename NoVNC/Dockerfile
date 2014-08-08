#
# Ubuntu Desktop (Gnome) Dockerfile
#
# https://github.com/intlabs/Docker-Ubuntu-Desktop-Gnome
#

# Install GNOME3 and VNC server.
# (c) Pete Birley

# Pull base image.
FROM dockerfile/ubuntu

# Setup enviroment variables
ENV DEBIAN_FRONTEND noninteractive

RUN \
	apt-get update  \
	&& apt-get upgrade -y  \
	&& apt-get update  \
	&& apt-get install libfuse2 -y  \
	&& cd /tmp ; apt-get download fuse  \
	&& cd /tmp ; dpkg-deb -x fuse_* .  \
	&& cd /tmp ; dpkg-deb -e fuse_*  \
	&& cd /tmp ; rm fuse_*.deb  \
	&& cd /tmp ; echo -en '#!/bin/bash\nexit 0\n' > DEBIAN/postinst  \
	&& cd /tmp ; dpkg-deb -b . /fuse.deb  \
	&& cd /tmp ; dpkg -i /fuse.deb \
	&& dpkg-divert --local --rename --add /sbin/initctl && ln -sf /bin/true /sbin/initctl  \
	&& apt-get install -y xorg gnome-core gnome-session-fallback tightvncserver libreoffice  \
	&& apt-get install -y supervisor expect \
	&& apt-get clean && apt-get autoremove  \
	&& mkdir -p /root/.vnc

ADD gnome-keybindings.pl /usr/local/etc/gnome-keybindings.pl
ADD gnome-docker-fix-and-customise.sh /usr/local/etc/gnome-docker-fix-and-customise.sh
ADD xstartup /root/.vnc/xstartup
ADD spawn-desktop.sh /usr/local/etc/spawn-desktop.sh
ADD start-vnc-expect-script.sh /usr/local/etc/start-vnc-expect-script.sh
ADD vnc.conf /etc/vnc.conf
ADD noVNC /noVNC/
ADD supervisord.conf /etc/

RUN \
	chmod +x /usr/local/etc/gnome-keybindings.pl \
	&& chmod +x /usr/local/etc/gnome-docker-fix-and-customise.sh \
	&& chmod 755 /root/.vnc/xstartup \
	&& chmod +x /usr/local/etc/spawn-desktop.sh \
	&& chmod +x /usr/local/etc/start-vnc-expect-script.sh

# Define mountable directories.
VOLUME ["/data"]

# Define default command.
CMD ["/usr/local/etc/spawn-desktop.sh"]

# Expose ports.
EXPOSE 6080

