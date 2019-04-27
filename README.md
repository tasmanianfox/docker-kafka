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



## Production

__Warning:__ this image is NOT tested in Production by author.