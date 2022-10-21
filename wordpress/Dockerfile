FROM wordpress:latest

COPY wp /usr/local/bin/wp
COPY custom.ini $PHP_INI_DIR/conf.d/
COPY config.yml /var/www/config.yml

RUN pecl install xdebug-3.1.5 > /dev/null 2>&1

ENV WP_CLI_CONFIG_PATH='/var/www/config.yml'

RUN addgroup --gid 1000 wordpress \
    && adduser --disabled-password --gecos "" --force-badname --uid 1000 --gid 1000 wordpress \
    && echo  "Create logs directory: " \
    && mkdir -p /var/www/logs/ \
    && echo  "done. " \
    && echo  "Create log files: " \
    && touch /var/www/logs/xdebug.log \
    && touch /var/www/logs/wp-debug.log \
    && echo  "done. " \
    && echo  "Fixing permissions: " \
    && chmod -R 777 /var/www/ /usr/local/bin/wp \
    && chown -R wordpress:wordpress /var/www/ \
    && echo  "done. "

USER wordpress

