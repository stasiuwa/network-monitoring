FROM postgres:16-alpine

LABEL org.opencontainers.image.description="PostgreSQL for log backup"

ENV POSTGRES_DB=networkmonitoring
ENV POSTGRES_USER=admin
ENV POSTGRES_PASSWORD=admin

COPY init.sql /docker-entrypoint-initdb.d/