FROM ubuntu
RUN apt-get update && apt-get install -y supervisor
RUN mkdir -p /var/log/supervisor
RUN apt install -y nginx
RUN apt-get install php8.3-fpm -y
RUN rm /etc/nginx/sites-enabled/default
#COPY index.php /var/www/html/index.php
COPY supervisord.conf /etc/supervisor/conf.d/supervisord.conf
COPY nginx.conf /etc/nginx/sites-enabled/nginx.conf
EXPOSE 80
CMD ["/usr/bin/supervisord", "-c", "/etc/supervisor/conf.d/supervisord.conf"]