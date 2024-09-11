# Kafka setup guide to generate streaming events

## Introduction

In this guide, we'll walk through setting up Apache Kafka using Docker. We'll configure both a **Producer** and a **Consumer** to send and receive events, simulating real-time event generation and processing. This setup will allow you to effectively test and run your streaming applications.

Objectives:

- Set up Kafka and Zookeeper using Docker.
- Create a Producer that generates streaming events.
- Set up a Consumer that processes those events.
- Simulate real-time event generation and consumption.


**Prerequisites**

Make sure to have Docker Compose installed to manage and run Kafka and Zookeeper containers. You can find the Docker Compose configuration to set up Kafka and Zookeeper in this link: [docker-compose-img](https://github.com/aleixcastellvi/docker-compose-img)

## Start up

**Step 1**. Start Kafka and Zookeeper

To launch Kafka and Zookeeper using Docker, navigate to the directory where your docker-compose.yml is located and run the following command:

```bash
docker-compose up -d
```

You can also launch the container from the Docker Desktop interface.

<u>Check Running Containers</u>

Now, use the following command to view all active containers:

```bash
docker ps
```

Identify the Kafka container's name. In this example, we'll use `kafka-broker-1`.

**Step 2**. Access the Kafka Container

To execute Kafka commands from within the container, use the following command, replacing `kafka-broker-1` with the actual name of your Kafka container:

```bash
docker exec -it kafka-broker-1 bash
```

This command gives you access to the Kafka environment inside the container.

**Step 3**. Configure a Kafka Topic

<u>Create a topic</u>

Run the following command inside the Kafka container (Step 2) to create a new topic. Replace <topic-name> with your desired topic name. In this case, the topic will have 3 partitions and a replication factor of 1:

```bash
kafka-topics.sh --create --topic <topic-name> --bootstrap-server kafka-broker-1:9092 --partitions 3 --replication-factor 1
```

<u>List all topics</u>

To view all the available topics, use:

```bash
kafka-topics.sh --list --bootstrap-server kafka-broker-1:9092
```

<u>Delete a topic</u>

To remove a topic, run:

```bash
kafka-topics.sh --delete --topic <topic-name> --bootstrap-server kafka-broker-1:9092
```

## Create a Kafka Producer

To send messages to the Kafka topic, start a producer on the created topic (<topic-name>). This command will allow you to type messages directly in the terminal:

```bash
kafka-console-producer.sh --topic <topic-name> --bootstrap-server kafka-broker-1:9092
```

Simply type your message and press Enter. The message will be sent to the Kafka topic.

## Create a Kafka Consumer

To start a consumer that listens for messages on the same topic (<topic-name>), use this command. The --from-beginning option allows the consumer to read messages from the start:

```bash
kafka-console-consumer.sh --topic <topic-name> --bootstrap-server kafka-broker-1:9092 --from-beginning
```

As messages are produced, the consumer will display them in real-time.