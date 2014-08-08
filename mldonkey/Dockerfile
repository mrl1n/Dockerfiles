FROM ubuntu:14.04 

# Set the file maintainer (your name - the file's author)
MAINTAINER Dominic Giebert <giebert@in.tum.de>

RUN apt-get update && apt-get install -y --force-yes --no-install-recommends supervisor telnet mldonkey-server

ADD config /.mldonkey/
ADD supervisor.conf /etc/

VOLUME ["/.mldonkey/shared/"]
# Port to expose
EXPOSE 4444

# Set the CMD
CMD ["/usr/bin/supervisord", "-n", "-c", "/etc/supervisor.conf"]

