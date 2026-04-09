FROM debian:stable-slim AS filebeat-builder

RUN apt-get update && apt-get install -y curl tar \
    && rm -rf /var/lib/apt/lists/*

WORKDIR /tmp

RUN curl -L -O https://artifacts.elastic.co/downloads/beats/filebeat/filebeat-9.3.3-linux-x86_64.tar.gz \
    && tar xzf filebeat-9.3.3-linux-x86_64.tar.gz

FROM debian:stable-slim

LABEL org.opencontainers.image.title="Network Monitoring Stack"
LABEL org.opencontainers.image.description="Suricata + Filebeat"

RUN apt-get update && apt-get install -y \
    suricata \
    supervisor \
    net-tools \
    iproute2 \
    gnupg \
    wget \
    ca-certificates \
    && rm -rf /var/lib/apt/lists/*

COPY --from=filebeat-builder /tmp/filebeat-9.3.3-linux-x86_64 /opt/filebeat

RUN mkdir -p /var/log/suricata \
    && mkdir -p /var/lib/filebeat \
    && mkdir -p /var/log/supervisor

COPY suricata.yaml /etc/suricata/suricata.yaml
COPY filebeat.yml /opt/filebeat/filebeat.yml
COPY supervisord.conf /etc/supervisor/conf.d/supervisord.conf

USER root

CMD ["/usr/bin/supervisord"]