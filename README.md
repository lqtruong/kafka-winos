# Kafka docker for Windows OS

- Download the Zookeeper from page https://zookeeper.apache.org/releases.html (3.5.8)
- Download the Kafka from page https://kafka.apache.org/downloads (kafka_2.13-2.6.0)
# Start Zookeeper 
- Configure Zookeeper Admin (in `/conf/zoo.cfg` file) netty server port to `admin.serverPort=8099`. This to avoid the App default port 8080 conflict later
- Run command to start `./zkServer.cmd start`

# Stop Zookeeper 
- Run command to stop: `./zkServer.cmd stop`

# Start Kafka
- Configure Kafka (in `/config/zookeeper.properties` file) with the Zookeeper admin port (e.g admin.serverPort=8099)
- Run command to start `./kafka-server-start.bat ../../config/server.properties`

# Stop Kafka
- Run command to stop: `./kafka-server-stop.bat`

## Topics
- Run command to create a topic: `./kafka-topics.bat --create --zookeeper localhost:2181 --replication-factor 1 --partitions 1 --topic test_truong`
- Run command to list all topics: `./kafka-topics.bat --list --zookeeper localhost:2181`

## Test Topics
- Run command to verify if a topic was created: `./kafka-topics.bat --describe --topic test_truong --bootstrap-server localhost:9092`
- Open terminal to create an event to the topic: `./kafka-console-producer.bat --topic test_truong --bootstrap-server localhost:9092`
- Open terminal to read the event from the topic: `./kafka-console-consumer.bat --topic test_truong --from-beginning --bootstrap-server localhost:9092`

## Practical
- Write some events into the Topic (at `kafka-console-producer` terminal): **This is truong event**
- Will see the events printed out from reading by the consumer (at `kafka-console-consumer` terminal) => **This is truong event**

Happy coding!
