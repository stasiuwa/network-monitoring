FROM zabbix/zabbix-server-pgsql:alpine-7.4-latest

LABEL org.opencontainers.image.title="Zabbix Server"

ENV DB_SERVER_HOST=postgres
ENV POSTGRES_DB=networkmonitoring
ENV POSTGRES_USER=admin
ENV POSTGRES_PASSWORD=admin
ENV ZBX_TIMEOUT=10