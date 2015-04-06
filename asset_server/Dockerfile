
FROM tenforward/centos-i386

# Set the file maintainer (your name - the file's author)
MAINTAINER Dominic Giebert <giebert@in.tum.de>

RUN yum install -y python-setuptools
RUN easy_install supervisor
RUN mkdir /etc/supervisord.d/
RUN wget http://unity3d.com/files/asset-server/unity_asset_server-2.0.1.i386.rpm
RUN rpm -Uvh unity_asset_server-2.0.1.i386.rpm
RUN rm unity_asset_server-2.0.1.i386.rpm

ADD configure /
ADD backup /
ADD supervisord.conf /etc/
ADD supervisor.conf /etc/supervisord.d/
ADD reset_admin_password_fix /opt/unity_asset_server/bin/

VOLUME ["/var/backup"]
# Port to expose
EXPOSE 10733

# Set the CMD

CMD ["/usr/bin/supervisord", "-n", "-c", "/etc/supervisord.conf"]
