# NYC Camp Symfony NGINX Image
#
# VERSION 0.0.1

FROM debian:stable
MAINTAINER skriptble <kris.brandow@gmail.com>

RUN apt-get update
RUN yes | apt-get install -y php5 php5-fpm php-pear php5-common php5-mcrypt php5-mysql php5-cli php5-gd php5-intl php5-curl php5-dev

ADD www.conf /etc/php5/fpm/pool.d/www.conf
ADD php-fpm.conf /etc/php5/fpm/php-fpm.conf

EXPOSE 9000
VOLUME ["/app"]

CMD ["/usr/sbin/php5-fpm"]
