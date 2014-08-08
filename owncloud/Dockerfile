FROM debian

#ADD . /usr/src/app
#WORKDIR /usr/src/app

# install your application's dependencies
RUN apt-get update \
	&& apt-get install -y wget \
 	&& wget http://download.opensuse.org/repositories/isv:ownCloud:community/Debian_7.0/Release.key \
	&& apt-key add - < Release.key  \
	&& echo 'deb http://download.opensuse.org/repositories/isv:/ownCloud:/community/Debian_7.0/ /' >> /etc/apt/sources.list.d/owncloud.list \
	&& apt-get update \
	&& apt-get install -y owncloud python-setuptools \
	&& easy_install supervisor \
 	&& mkdir /etc/supervisord.d/ \
	&& a2enmod ssl \
	&& a2ensite default-ssl \
	&& a2enmod rewrite

ADD configure /
ADD supervisord.conf /etc/
ADD supervisor.conf /etc/supervisord.d/

# replace this with your application's default port
#EXPOSE 80
EXPOSE 443

ENV APACHE_RUN_USER  www-data
ENV APACHE_RUN_GROUP www-data
ENV APACHE_LOG_DIR   /var/log/apache2
ENV APACHE_RUN_DIR   /etc/apache2

CMD ["/usr/local/bin/supervisord", "-n", "-c", "/etc/supervisord.conf"]
