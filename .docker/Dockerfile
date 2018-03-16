FROM php:7.2-fpm
MAINTAINER Piero recchia <pierorecchia.com>

RUN apt-get update && apt-get install -y  zlib1g-dev libicu-dev libpq-dev imagemagick git mysql-client wget unzip\
	&& docker-php-ext-install opcache \
	&& docker-php-ext-install intl \
	&& docker-php-ext-install pdo_mysql \
	&& php -r "readfile('https://getcomposer.org/installer');" | php -- --install-dir=/usr/local/bin --filename=composer \
	&& chmod +sx /usr/local/bin/composer

RUN version=$(php -r "echo PHP_MAJOR_VERSION.PHP_MINOR_VERSION;") \
    && curl -A "Docker" -o /tmp/blackfire-probe.tar.gz -D - -L -s https://blackfire.io/api/v1/releases/probe/php/linux/amd64/$version \
    && tar zxpf /tmp/blackfire-probe.tar.gz -C /tmp \
    && mv /tmp/blackfire-*.so $(php -r "echo ini_get('extension_dir');")/blackfire.so \
    && printf "extension=blackfire.so\nblackfire.agent_socket=tcp://blackfire:8707\n" > $PHP_INI_DIR/conf.d/blackfire.ini

RUN cd /tmp && wget https://github.com/phpredis/phpredis/archive/master.zip -O phpredis.zip \
    && unzip -o /tmp/phpredis.zip && mv /tmp/phpredis-* /tmp/phpredis && cd /tmp/phpredis \
    && phpize && ./configure && make && make install \
    && printf "extension=redis.so" > $PHP_INI_DIR/conf.d/redis.ini

EXPOSE 9000