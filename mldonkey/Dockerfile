
FROM centos

# Set the file maintainer (your name - the file's author)
MAINTAINER Dominic Giebert <giebert@in.tum.de>

RUN yum install -y python-setuptools
RUN easy_install supervisor
RUN mkdir /etc/supervisord.d/
RUN yum install -y wget
RUN wget http://dl.fedoraproject.org/pub/epel/6/x86_64/epel-release-6-8.noarch.rpm
RUN wget http://rpms.famillecollet.com/enterprise/remi-release-6.rpm
RUN rpm -Uvh remi-release-6*.rpm epel-release-6*.rpm
RUN yum install -y mldonkey-server

ADD configure /
ADD supervisord.conf /etc/
ADD supervisor.conf /etc/supervisord.d/

VOLUME ["/var/backup"]
# Port to expose
EXPOSE 10733

# Set the CMD
CMD ["/usr/bin/supervisord", "-n", "-c", "/etc/supervisord.conf"]
