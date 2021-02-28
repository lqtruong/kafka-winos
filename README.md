# Kafka docker for Windows OS

- Download the Kafka from page https://kafka.apache.org/downloads (kafka_2.13-2.7.0)
# Start Zookeeper 
- Run command to start `.\bin\windows\zookeeper-server-start.bat .\config\zookeeper.properties`

# Stop Zookeeper 
- Run command to stop: `.\bin\windows\zookeeper-server-stop.bat`

# Start Kafka
- Run command to start `.\bin\windows\kafka-server-start.bat .\config\server.properties`

# Stop Kafka
- Run command to stop: `.\bin\windows\kafka-server-stop.bat`

## Topics
- Run command to create a topic: `.\bin\windows\kafka-topics.bat --create --topic test_truong --replication-factor 1 --partitions 1 --bootstrap-server localhost:9092`
- Run command to list all topics: `.\bin\windows\kafka-topics.bat --list --zookeeper localhost:2181`

## Delete a Topic
- Enable deletion possibility on kafka server: `delete.topic.enable=true` in `.\config\server.properties`
- Run command to delete a topic: `.\bin\windows\kafka-topics.bat --delete --topic test_truong --bootstrap-server localhost:9092`

## Test Topics
- Run command to verify if a topic was created: `./kafka-topics.bat --describe --topic test_truong --bootstrap-server localhost:9092`
- Open terminal to create an event to the topic: `./kafka-console-producer.bat --topic test_truong --bootstrap-server localhost:9092`
- Open terminal to read the event from the topic: `./kafka-console-consumer.bat --topic test_truong --from-beginning --bootstrap-server localhost:9092`

## Practical
- Write some events into the Topic (at `kafka-console-producer` terminal): **This is truong event**
- Will see the events printed out from reading by the consumer (at `kafka-console-consumer` terminal) => **This is truong event**

Happy coding!
