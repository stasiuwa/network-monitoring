FROM debian:stable-slim

LABEL org.opencontainers.image.title="Network Monitoring Stack"
LABEL org.opencontainers.image.description="Suricata + Filebeat"

RUN apt-get update && apt-get install -y \
    suricata \
    curl \
    supervisor \
    net-tools \
    iproute2 \
    gnupg \
    wget \
    ca-certificates \
    && rm -rf /var/lib/apt/lists/*

RUN curl -L -O https://artifacts.elastic.co/downloads/beats/filebeat/filebeat-8.13.4-linux-x86_64.tar.gz \
    && tar xzf filebeat-8.13.4-linux-x86_64.tar.gz \
    && mkdir -p /opt/filebeat \
    && cp -r filebeat-8.13.4-linux-x86_64/* /opt/filebeat \
    && rm -rf filebeat-8.13.4-linux-x86_64*

RUN mkdir -p /var/log/suricata \
    && mkdir -p /var/lib/filebeat \
    && mkdir -p /var/log/supervisor

COPY suricata.yaml /etc/suricata/suricata.yaml
COPY filebeat.yml /opt/filebeat/filebeat.yml
COPY supervisord.conf /etc/supervisor/conf.d/supervisord.conf

USER root

CMD ["/usr/bin/supervisord"]