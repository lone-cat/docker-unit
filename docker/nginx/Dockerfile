FROM nginx:latest
MAINTAINER Alex <alex@melentev.net>

COPY conf/fastcgi_params /etc/nginx/fastcgi_params
COPY conf/conf.d /etc/nginx/conf.d
COPY conf/proxy.params.conf /etc/nginx/proxy.params.conf

WORKDIR /app