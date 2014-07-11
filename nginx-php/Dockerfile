FROM ubuntu:trusty

MAINTAINER skriptble <kris.brandow@gmail.com>

# Install packages
RUN apt-get update
RUN apt-get install nginx php5-fpm php5-mysql supervisor -y

# Make log directory
RUN mkdir -p /var/log/supervisor

# Add configuration files
ADD default.conf /etc/nginx/sites-available/default
ADD date-time.conf /etc/php5/fpm/conf.d/date_time.ini
ADD supervisord.conf /etc/supervisor/conf.d/supervisord.conf

# Ensure NGINX runs in foreground mode
RUN echo "\ndaemon off;" >> /etc/nginx/nginx.conf

EXPOSE 80

CMD ["/usr/bin/supervisord"]
