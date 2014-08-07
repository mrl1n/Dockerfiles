
FROM phusion/baseimage 

# Set the file maintainer (your name - the file's author)
MAINTAINER Dominic Giebert <giebert@in.tum.de>

RUN apt-get update
RUN apt-get install -y python-setuptools
RUN easy_install supervisor
RUN mkdir /etc/supervisord.d/
RUN apt-get install -y wget
RUN apt-get install -y mldonkey-server

ADD configure /
ADD supervisord.conf /etc/
ADD supervisor.conf /etc/supervisord.d/

VOLUME ["/var/backup"]
# Port to expose
EXPOSE 10733

# Set the CMD
CMD ["/usr/bin/supervisord", "-n", "-c", "/etc/supervisord.conf"]
