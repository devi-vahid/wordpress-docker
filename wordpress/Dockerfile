FROM wordpress:latest
RUN addgroup --gid 1024 wordpress
RUN adduser --disabled-password --gecos "" --force-badname --gid 1024 wordpress
USER wordpress
COPY custom.ini $PHP_INI_DIR/conf.d/