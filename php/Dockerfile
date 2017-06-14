FROM neiron/docker-php:latest

RUN apt-get update \
	&& apt-get install -y php-xdebug php-geoip geoip-database-extra php-pear \
	&& rm -rf /var/lib/apt/lists/*

ENV INI_CONF=/etc/php/7.1

RUN sed -i "s/display_errors = Off/display_errors = On/" $INI_CONF/cli/php.ini
RUN sed -i "s/display_startup_errors = Off/display_startup_errors = On/" $INI_CONF/cli/php.ini
RUN symfony self-update
RUN wget http://www.phing.info/get/phing-latest.phar
RUN chmod +x phing-latest.phar
RUN mv phing-latest.phar /usr/local/bin/phing

COPY xdebug.ini $INI_CONF/mods-available/

EXPOSE 22

WORKDIR /usr/share/nginx/www