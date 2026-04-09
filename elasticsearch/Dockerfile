FROM docker.elastic.co/elasticsearch/elasticsearch:9.3.3

LABEL org.opencontainers.image.description="Elasticsearch node"

ENV discovery.type=single-node
ENV ES_JAVA_OPTS="-Xms512m -Xmx512m"
ENV xpack.security.enabled=false