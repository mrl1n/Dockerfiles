FROM debian

#ADD . /usr/src/app
#WORKDIR /usr/src/app

# install your application's dependencies
RUN apt-get update
RUN apt-get install -y wget
RUN wget http://download.opensuse.org/repositories/isv:ownCloud:community/Debian_7.0/Release.key
RUN apt-key add - < Release.key  
RUN echo 'deb http://download.opensuse.org/repositories/isv:/ownCloud:/community/Debian_7.0/ /' >> /etc/apt/sources.list.d/owncloud.list 
RUN apt-get update
RUN apt-get install -y owncloud

RUN a2enmod ssl
RUN a2ensite default-ssl
RUN a2enmod rewrite

ADD init /
# replace this with your application's default port
#EXPOSE 80
EXPOSE 443

VOLUME ["/var/www/owncloud/data", "/var/www/owncloud/config"]

CMD ["/init", "-DFOREGROUND"]
