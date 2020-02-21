FROM alpine:3.10
LABEL AUTOR="Capgemini" PROYECTO="APACHE KAFKA"
ENV ZOOKEEPER_URL=https://archive.apache.org/dist/zookeeper/zookeeper-3.5.7/apache-zookeeper-3.5.7.tar.gz
RUN apk add --update --no-cache gawk openjdk11 bash curl && mkdir -p /opt/zookeeper /opt/zookeeper-data
RUN curl $ZOOKEEPER_URL --output /tmp/zookeeper.tgz && tar zxvf /tmp/zookeeper.tgz --strip-components 1 -C /opt/zookeeper && \
touch /opt/zookeeper/conf/zoo.cfg && rm -rf /tmp/zookeeper.tgz
RUN chmod +x /opt/zookeeper/bin/* && \
chown -R 1001 /opt && \
chgrp -R 0 /opt && \
chmod -R g=u /opt
USER 1001
EXPOSE 2181 2888 3888 9998
WORKDIR /opt/zookeeper