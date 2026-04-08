FROM debian:stable-slim

LABEL org.opencontainers.image.title="Network Monitoring Stack"
LABEL org.opencontainers.image.description="Suricata -> Filebeat + Zabbix Agent - Host simulation"
#LABEL org.opencontainers.image.source="https://github.com/networkmonitoring"

#SURYKATA
RUN apt-get update && apt-get install -y \
    suricata \
    curl \
    supervisor \
    net-tools \
    iproute2 \
    && rm -rf /var/lib/apt/lists/*

#FILEBEAT
RUN curl -L -O https://artifacts.elastic.co/downloads/beats/filebeat/filebeat-8.12.0-linux-x86_64.tar.gz \
    && tar xzf filebeat-*.tar.gz \
    && mv filebeat-* /opt/filebeat \
    && rm filebeat-*.tar.gz

#ZABBIX AGENTURA
# wget https://repo.zabbix.com/zabbix/7.4/release/debian/pool/main/z/zabbix-release/zabbix-release_latest_7.4+debian10_all.deb
# dpkg -i zabbix-release_latest_7.4+debian10_all.deb
# apt update
# apt install zabbix-agent2
# apt install zabbix-agent2-plugin-mongodb zabbix-agent2-plugin-mssql zabbix-agent2-plugin-postgresql
# systemctl restart zabbix-agent2
# systemctl enable zabbix-agent2

COPY suricata.yaml /etc/suricata/suricata.yaml
COPY filebeat.yaml /opt/filebeat/filebeat.yaml
COPY zabbix_agentd.conf /etc/zabbix/zabbix_agentd.conf
COPY supervisord.conf /etc/supervisior/conf.d/supervisor.conf

RUN useradd -m appuser && chown -R appuser:appuser /opt /etc/suricata

USER appuser

EXPOSE 10050

ENTRYPOINT ["/usr/bin/supervisord"]