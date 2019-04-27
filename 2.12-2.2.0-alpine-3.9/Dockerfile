FROM alpine:3.9

RUN wget https://www-eu.apache.org/dist/kafka/2.2.0/kafka_2.12-2.2.0.tgz
RUN tar -xf kafka_2.12-2.2.0.tgz
RUN mv kafka_2.12-2.2.0 /opt/kafka
RUN rm kafka_2.12-2.2.0.tgz

ADD launcher.sh /opt/launcher.sh

RUN apk add --no-cache bash openjdk8-jre

CMD bash /opt/launcher.sh /opt/kafka/server.properties