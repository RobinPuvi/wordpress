FROM wordpress:5.1-fpm-alpine
FROM postgres:12.4-alpine
FROM nginx:1.18-alpine

RUN apt-get update && apt-get install -y libpq-dev
RUN apt install php-fpm
RUN docker-php-ext-configure pgsql -with-pgsql=/usr/local/pgsql
RUN docker-php-ext-install pdo pdo_pgsql

RUN mkdir -p /var/lib/postgresql/data
ENV PGDATA /var/lib/postgresql/data

COPY ./wp-content /var/www/html/wp-content

RUN chmod -R 755 /var/www/html/
RUN chown www-data:www-data -R /var/www/html/

VOLUME /var/www/html