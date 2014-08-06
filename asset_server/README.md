Unity Asset Server
===========

Based on tenforward/centos-i386

RPM Used: http://unity3d.com/unity/collaboration

Uses a cronjob to backup the Database every 5 mins

Github: https://github.com/mrl1n/Dockerfiles
Usage:
-----------

Setup:

docker run -d -p 10733:10733 -e PASSWORD=$( read -p "Password: " -s PASSWORD && echo $PASSWORD ) -v /var/asset_server/:/var/backup/:rw mrl1n/unity-asset-server

Usage:

docker run -d -p 10733:10733 -v /var/asset_server/:/var/backup/:rw mrl1n/unity-asset-server


TODO:
-----------

- Only write on changes
