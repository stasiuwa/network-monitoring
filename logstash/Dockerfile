FROM docker.elastic.co/logstash/logstash:9.3.3

LABEL org.opencontainers.image.description="Logstash for Suricata logs"

RUN rm -f /usr/share/logstash/pipeline/logstash.conf

COPY pipeline/ /usr/share/logstash/pipeline/
COPY config/ /usr/share/logstash/config/

USER logstash