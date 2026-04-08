FROM zabbix/zabbix-web-nginx-pgsql:alpine-7.4-latest

LABEL org.opencontainers.image.title="Zabbix Web"

ENV DB_SERVER_HOST=postgres
ENV POSTGRES_DB=networkmonitoring
ENV POSTGRES_USER=admin
ENV POSTGRES_PASSWORD=admin
ENV ZBX_SERVER_HOST=zabbix-server
ENV PHP_TZ=Europe/Warsaw