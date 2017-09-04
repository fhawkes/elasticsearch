FROM docker.elastic.co/elasticsearch/elasticsearch:5.5.1

MAINTAINER Floyd Hawkes <floydhawkes@gmail.com>

ENV HOME=/opt/app-root/src \
  JAVA_VER=1.8.0 \
  ES_CONF=/usr/share/elasticsearch/config/elasticsearch.yml \
  ELASTICSEARCH_CLUSTER_NAME=default-cluster \
  ELASTICSEARCH_MAX_MEMORY=1G \
  ELASTICSEARCH_LOG_LEVEL=INFO

LABEL io.k8s.description="Elasticsearch container for allowing indexing and searching of aggregated logs" \
  io.k8s.display-name="Elasticsearch 5.5.1" \
  io.openshift.expose-services="9200:https, 9300:https" \
  io.openshift.tags="cache,database,search,elasticsearch"

RUN mkdir -p /elasticsearch/persistent && \
    chown -R 1001:0 /elasticsearch /usr/share/elasticsearch && \
    chmod -R og+rwx /elasticsearch

COPY container-entrypoint /usr/bin/
COPY elasticsearch.yml /etc/elasticsearch/

EXPOSE 9200
EXPOSE 9300
USER 1001

ENTRYPOINT ["container-entrypoint"]

CMD ["/usr/share/elasticsearch/bin/elasticsearch"]
