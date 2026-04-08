FROM docker.elasitc.co/logstash/logstash:9.3.3

LABEL org.opencontainers.image.description="Logstash for Suricata logs"

# RUN rm -f /usr/share/logstash/pipeline/logstash.conf

COPY logstash/pipeline/ /usr/share/logstash/pipeline/
COPY logstash/config/ /usr/share/logstash/config/

RUN chmod -R 755 /usr/share/logstash/pipeline

USER logstash