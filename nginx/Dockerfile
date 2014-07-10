# NYC Camp Symfony NGINX Image
#
# VERSION 0.0.1

FROM nginx
MAINTAINER skriptble <kris.brandow@gmail.com>

ADD nginx.conf /etc/nginx.conf
# COPY app /app
# ADD authentication-site.conf /etc/nginx/sites-enabled/authentication-site.conf
ADD static-site.conf /etc/nginx/sites-enabled/static-site.conf

EXPOSE 80
