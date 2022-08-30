FROM wordpress:latest

COPY wp /usr/local/bin/wp
RUN chmod +x /usr/local/bin/wp

RUN pecl install xdebug-3.1.5 > /dev/null 2>&1

COPY custom.ini $PHP_INI_DIR/conf.d/

RUN addgroup --gid 1024 wordpress \
    && adduser --disabled-password --gecos "" --force-badname --gid 1024 wordpress
USER wordpress
