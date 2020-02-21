FROM alpine:3.10
LABEL AUTOR="Capgemini" PROYECTO="APACHE KAFKA"
ENV KAFKA_URL=https://archive.apache.org/dist/kafka/2.4.0/kafka_2.13-2.4.0.tgz
RUN apk add --update --no-cache gawk openjdk11 bash curl && mkdir -p /opt/kafka /opt/kafka-storage
RUN curl $KAFKA_URL --output /tmp/kafka.tgz && tar zxvf /tmp/kafka.tgz --strip-components 1 -C /opt/kafka && rm -rf /tmp/*.tgz
COPY log4j.properties /opt/kafka/config
COPY checkZoo /opt/checkZoo
RUN chmod +x /opt/checkZoo && chown 1001 -R /opt && \
chgrp -R 0 /opt && \
chmod -R g=u /opt
USER 1001
EXPOSE 9092 9093 7071 9999 9998
WORKDIR /opt/kafka/bin