FROM docker.io/nginx:stable
RUN rm /etc/nginx/conf.d/*
ADD nginx.conf /etc/nginx/conf.d/
RUN mkdir -p /var/www/html
ADD style.css /var/www/html/
RUN chmod 444 /var/www/html/style.css