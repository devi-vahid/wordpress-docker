FROM wordpress:latest

COPY wp /usr/local/bin/wp
RUN chmod +x /usr/local/bin/wp

RUN pecl install xdebug-3.1.5 > /dev/null 2>&1

COPY custom.ini $PHP_INI_DIR/conf.d/

RUN addgroup --gid 1000 wordpress \
    && adduser --disabled-password --gecos "" --force-badname --uid 1000 --gid 1000 wordpress \
    && chmod -R 755 /var/www/html/ \
    && chown -R wordpress:wordpress /var/www/html/
USER wordpress

