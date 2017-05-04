FROM neiron/docker-php:latest

RUN apt-get update \
	&& apt-get install -y php-xdebug php-geoip geoip-database-extra \
	&& rm -rf /var/lib/apt/lists/*

ENV INI_CONF=/etc/php/7.1

RUN sed -i "s/display_errors = Off/display_errors = On/" $INI_CONF/cli/php.ini
RUN sed -i "s/display_startup_errors = Off/display_startup_errors = On/" $INI_CONF/cli/php.ini
RUN symfony self-update

COPY xdebug.ini $INI_CONF/mods-available/

EXPOSE 9000 9010 22

WORKDIR /usr/share/nginx/www