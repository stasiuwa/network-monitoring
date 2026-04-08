FROM debian:stable-slim

LABEL org.opencontainers.image.title="Network Monitoring Stack"
LABEL org.opencontainers.image.description="Suricata + Filebeat + Zabbix Agent"

# pakiety systemowe i surykata
RUN apt-get update && apt-get install -y \
    suricata \
    curl \
    supervisor \
    net-tools \
    iproute2 \
    gnupg \
    && rm -rf /var/lib/apt/lists/*

# Filebeat
RUN curl -L -O https://artifacts.elastic.co/downloads/beats/filebeat/filebeat-8.12.0-linux-x86_64.tar.gz \
    && tar xzf filebeat-*.tar.gz \
    && mv filebeat-* /opt/filebeat \
    && rm filebeat-*.tar.gz

# Zabbix Agent
RUN curl -L -O https://repo.zabbix.com/zabbix/6.4/debian/pool/main/z/zabbix/zabbix-agent_6.4.0-1_amd64.deb \
    && apt-get update && apt-get install -y ./zabbix-agent_6.4.0-1_amd64.deb \
    && rm zabbix-agent_6.4.0-1_amd64.deb

RUN mkdir -p /var/log/suricata

COPY suricata.yaml /etc/suricata/suricata.yaml
COPY filebeat.yml /opt/filebeat/filebeat.yml
COPY zabbix_agentd.conf /etc/zabbix/zabbix_agentd.conf
COPY supervisord.conf /etc/supervisor/conf.d/supervisord.conf

RUN useradd -m appuser && \
    chown -R appuser:appuser /opt /etc/suricata /var/log/suricata

USER appuser

EXPOSE 10050

ENTRYPOINT ["/usr/bin/supervisord"]