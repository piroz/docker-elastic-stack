FROM docker.elastic.co/kibana/kibana:6.6.0

RUN bin/kibana-plugin install https://github.com/johtani/analyze-api-ui-plugin/releases/download/6.6.0/analyze-api-ui-plugin-6.6.0.zip

ENV DOCKERIZE_VERSION v0.6.1

RUN curl -L -O https://github.com/jwilder/dockerize/releases/download/${DOCKERIZE_VERSION}/dockerize-linux-amd64-${DOCKERIZE_VERSION}.tar.gz

USER 0

RUN ["/bin/bash", "-c", "tar zxf dockerize-linux-amd64-${DOCKERIZE_VERSION}.tar.gz -C /usr/local/bin"]

RUN ["chown", "kibana:root", "/usr/local/bin/dockerize"]

USER kibana

RUN rm dockerize-linux-amd64-${DOCKERIZE_VERSION}.tar.gz

RUN ["ls", "-la", "/usr/local/bin/"]

CMD ["/usr/local/bin/dockerize", "--wait", "http://elasticsearch:9200", "-timeout", "60s", "-wait-retry-interval", "30s", "/usr/local/bin/kibana-docker"]