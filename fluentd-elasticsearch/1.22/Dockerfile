FROM gcr.io/google_containers/fluentd-elasticsearch:1.22

MAINTAINER singula

COPY ./td-agent.conf /etc/td-agent/td-agent.conf

RUN chmod 500 /etc/td-agent/td-agent.conf

# runtime environment variable
ENV ELASTICSEARCH_HOST_NAME="elasticsearch-logging" \
    LOGSTASH_PREFIX="logstash" \
    LOGSTASH_DATEFORMAT="%Y.%m.%d"

ENTRYPOINT []

CMD sed -i -e "s|host elasticsearch-logging|host ${ELASTICSEARCH_HOST_NAME}|" /etc/td-agent/td-agent.conf \
    && sed -i -e "s|logstash_prefix logstash|logs
