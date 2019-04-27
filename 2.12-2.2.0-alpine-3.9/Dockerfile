FROM alpine:3.9

ADD launcher.sh /opt/launcher.sh

RUN apk add --no-cache bash openjdk8-jre && \
    wget https://www-eu.apache.org/dist/kafka/2.2.0/kafka_2.12-2.2.0.tgz && \
    tar -xf kafka_2.12-2.2.0.tgz && \
    mv kafka_2.12-2.2.0 /opt/kafka && \
    rm kafka_2.12-2.2.0.tgz

CMD bash /opt/launcher.sh /opt/kafka/server.properties