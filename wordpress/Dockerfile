FROM wordpress:latest

COPY custom.ini $PHP_INI_DIR/conf.d/
COPY config.yml /var/www/config.yml

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
    && echo  "Installing xdebug-3.4.0: " \
    && pecl  install xdebug-3.4.0 > /dev/null 2>&1 \
    && echo  "Done " \
    && echo  "installing WP-CLI: " \
    && curl  -O https://raw.githubusercontent.com/wp-cli/builds/gh-pages/phar/wp-cli.phar > /dev/null 2>&1 \
    && mv    wp-cli.phar /usr/local/bin/wp \
    && echo  "Done. " \
    && echo  "Fixing permissions: " \
    && chmod -R 777 /var/www/ /usr/local/bin/wp \
    && chown -R wordpress:wordpress /var/www/ \
    && echo  "done. " 

USER wordpress
