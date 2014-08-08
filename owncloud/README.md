Owncloud 7
================

Basic Owncloud 7 Dockerfile from Debian repositories.


Usage:
-------

´´´
docker run -d -p 443:443 -p 80:80 -v /dir/:/var/www/owncloud/config -v /dir/:/var/www/owncloud/data mrl1n/owncloud7
´´´
