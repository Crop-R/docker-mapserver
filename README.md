# Docker image for mapserver 7.0

Here is a sample Dockerfile for using it:
```
FROM camptocamp/mapserver
MAINTAINER Camptocamp "info@camptocamp.com"

COPY *.map /etc/mapserver/
COPY *.sh *.env /docker-entrypoint.d/
```

Or you can use the image as is and mount volumes to customize it.


## Tunings

All the bash snipets in /docker-entrypoint.d ending with `.env` will
be sourced.

All the executable files in /docker-entrypoint.d ending with `.sh` will
be executed by the default entrypoint.

All the files ending with `.tmpl` in /etc/mapserver and /etc/apache2 (can be
changed by defining CONFD_DIRS in one of the sourced files) will go though
confd with the `env` backend. The TOML files are created automagically to
create a file at the same location, with just the `.tmpl` extension removed.
