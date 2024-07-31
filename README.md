# Apache Kafka Setup and Usage Guide
## What is Apache Kafka?
Apache Kafka is a distributed streaming platform designed for building real-time data pipelines and streaming applications. 
It operates on a publish-subscribe model, where producers send records to topics, which are then consumed by subscribers. 

Kafka's architecture is built for high throughput, fault tolerance, and scalability, making it ideal for handling large volumes of data across distributed systems. 
It's commonly used for message queuing, activity tracking, log aggregation, and stream processing. 

Kafka's ability to persistently store and replicate data across multiple servers ensures durability and reliability, while its low-latency performance allows it to process millions of messages per second. 
This makes Kafka a powerful tool for organizations dealing with real-time data streams and complex event processing. 

## Setup Instructions

1. Install Docker on your system.
2. Start Docker.
3. Create a folder named `kafka_setup`.
4. Create a virtual environment.
5. Use a `docker-compose.yml` file (ensure this file is in your `kafka_setup` folder).
6. Start Zookeeper and Kafka using the command:
   docker-compose up

## Checking Running Containers

In a new terminal tab, run:
docker ps
This will show the container IDs.

## Creating a Topic

1. Enter the Kafka container:
docker exec -it <container_id> /bin/bash

2. Navigate to the Kafka bin directory:
cd /opt/kafka/bin

3. Create a topic:
./kafka-topics.sh --create --topic test-topic --bootstrap-server localhost:9092 --replication-factor 1 --partitions 1

## Producing Messages

1. Run the Kafka console producer:
./kafka-console-producer.sh --topic test-topic --bootstrap-server localhost:9092

2. Type messages in the producer console.

## Consuming Messages

1. In a new terminal, enter the Kafka container again:
docker exec -it <container_id> /bin/bash

2. Navigate to the Kafka bin directory:
cd /opt/kafka/bin

3. Run the Kafka console consumer:
./kafka-console-consumer.sh --topic test-topic --bootstrap-server localhost:9092 --from-beginning

Messages typed in the producer console will be displayed in the consumer console.
