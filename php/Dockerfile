FROM docker.io/php:7.4-fpm
ADD index.php /var/www/html/
ADD process.php /var/www/html/
RUN chmod 444 /var/www/html/index.php && chmod 444 /var/www/html/process.php
RUN docker-php-ext-install mysqli