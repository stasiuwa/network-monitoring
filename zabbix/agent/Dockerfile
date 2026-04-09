FROM zabbix/zabbix-agent2:alpine-latest

LABEL org.opencontainers.image.title="Zabbix Agent"
LABEL org.opencontainers.image.description="Zabbix Agent2 container"

COPY zabbix_agent2.conf /etc/zabbix/zabbix_agent2.conf

EXPOSE 10050

CMD ["/usr/sbin/zabbix_agent2", "-f"]