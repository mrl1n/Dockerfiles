MLdonkey
===========

Based on the debian image

Adds a DCHUB

Usage:
-----------

```
docker run -ti -p 4080:4080 -p 1412:1412 -p 4545:4545 -v /mnt/finished/:/.mldonkey/shared/:rw  -e PASSWORD=$( read -p "Password: " -s PASSWORD && echo $PASSWORD ) -e IP="XXX.XXX.XXX.XXX" -e PORT="XXX" c5d1e3dd381b /bin/bash
```

TODO
-----------

- Make Data persistent
- Set Password on first start
- ...
