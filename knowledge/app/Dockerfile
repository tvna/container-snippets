FROM tomcat:9-jre8-alpine

ARG KNOWLEDGE_VERSION=1.13.1

RUN apk update && \
    apk add --no-cache --virtual .build-deps \
      ca-certificates \
      wget \
    && \
    apk add --no-cache --virtual .run-deps \
      dumb-init \
    && \
    rm -rf /usr/local/tomcat/webapps/ROOT && \
    wget https://github.com/support-project/knowledge/releases/download/v$KNOWLEDGE_VERSION/knowledge.war  -O /usr/local/tomcat/webapps/ROOT.war && \
    mkdir /root/.knowledge && \
    apk del .build-deps

VOLUME [ "/root/.knowledge" ]
EXPOSE 8080

CMD ["dumb-init", "/usr/local/tomcat/bin/catalina.sh", "run"]
