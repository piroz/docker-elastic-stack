FROM docker.elastic.co/logstash/logstash:6.6.0

ENV DOCKERIZE_VERSION v0.6.1

RUN curl -L -O https://github.com/jwilder/dockerize/releases/download/${DOCKERIZE_VERSION}/dockerize-linux-amd64-${DOCKERIZE_VERSION}.tar.gz

USER 0

RUN ["/bin/bash", "-c", "tar zxf dockerize-linux-amd64-${DOCKERIZE_VERSION}.tar.gz -C /usr/local/bin"]

RUN ["chown", "logstash:root", "/usr/local/bin/dockerize"]

USER logstash

RUN rm dockerize-linux-amd64-${DOCKERIZE_VERSION}.tar.gz

RUN ["ls", "-la", "/usr/local/bin/"]

CMD ["/usr/local/bin/dockerize", "--wait", "http://elasticsearch:9200", "-timeout", "60s", "-wait-retry-interval", "30s", "/usr/local/bin/docker-entrypoint"]