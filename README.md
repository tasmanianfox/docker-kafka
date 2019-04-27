# Dockerized Apache Kafka

## Development mode

### Notes

Since Apache Kafka depends on Zookeeper, the provided development configuration uses an official Zookeeper Docker image.

When using ```docker-compose.yaml```, Kafka and Zookeeper will start simultaneously. However, Kafka needs a working instance of Zookeeper, therefore Kafka will very likely restart at least once.

### Files

__.env__ - contains configuration for mounted volumes and ports. Please rename the _.env.dist_ file to _.env_ to proceed with installation of development environment

__docs/default_config__ - default configuration files for Kafka and Zookeeper. Feel free to copy and modify them.

__docker-compose.yaml__ - docker-compose configuration needed to run Zookeeper + Kafka

### Installation

1. Copy the _.env.dist_ config file to _.env_, change the config if needed.
1. Start Kafka+Zookeeper using ```docker-compose up``` command

### Testing

In this example the [Kafkacat](https://github.com/edenhill/kafkacat) utility is used to produce and consume messages.

```
# Terminal 1 (start the environment)
$ docker-compose up


# Terminal 2 (create a topic "persons")
$ docker-compose exec kafka bash
$ /opt/kafka/bin/kafka-topics.sh --create --topic persons --partitions 4 --replication-factor 1

# Terminal 3 (Produce a message)
$ kafkacat -b localhost:9092 -t persons -c1 -P
>>> Here you need to enter a simple message and press "enter"

# Terminal 4 (Consume a message)
$ kafkacat -b localhost:9092 -t persons -c10 -C
```

The output should be something like:
```
% Reached end of topic persons [0] at offset 0
John Doe
Jane Doe
% Reached end of topic persons [3] at offset 0
% Reached end of topic persons [1] at offset 2
% Reached end of topic persons [2] at offset 1
```



## Production

__Warning:__ this image is NOT tested in Production by author.
