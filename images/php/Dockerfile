FROM php:7.2-fpm-alpine

# lumen packages
RUN docker-php-ext-install mbstring tokenizer mysqli pdo_mysql

# Copy the app
COPY app /var/www/html/app
COPY app/.env /var/www/html/app/.env
#COPY app/.gitignore /var/www/html/app/.gitignore


ENV TIMEZONE Asia/Jakarta
ENV MYSQL_ROOT_PASSWORD root
ENV MYSQL_DATABASE appbilltax_DB789
ENV MYSQL_USER developer
ENV MYSQL_PASSWORD 123456
ENV MYSQL_USER_MONITORING monitoring
ENV MYSQL_PASSWORD_MONITORING monitoring



WORKDIR /var/www/html/app 
RUN php artisan migrate 
#RUN ./vendor/bin/phpunit --bootstrap vendor/autoload.php tests/TaxObjectBillsTest

#RUN echo "Docker is up"