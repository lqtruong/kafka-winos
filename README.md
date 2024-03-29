# Kafka Installation for Windows OS

- Download the Kafka from page https://kafka.apache.org/downloads (kafka_2.13-2.7.0)

# Config
Change the configuration in `.\config\server.properties` to enable the listeners, advertised.listeners and zookeeper.connect

```
listeners=PLAINTEXT://:9092

# Hostname and port the broker will advertise to producers and consumers. If not set, 
# it uses the value for "listeners" if configured.  Otherwise, it will use the value
# returned from java.net.InetAddress.getCanonicalHostName().
advertised.listeners=PLAINTEXT://localhost:9092
zookeeper.connect=localhost:2181
```

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
- Run command to list all topics: `.\bin\windows\kafka-topics.bat --list --bootstrap-server localhost:9092`

## Delete a Topic manually
- Enable deletion possibility on kafka server: `delete.topic.enable=true` in `.\config\server.properties`
- Run command to delete a topic: `.\bin\windows\kafka-topics.bat --delete --topic test_truong --bootstrap-server localhost:9092`
- Hints: `possibly, stop the kafka server. We can go to the temporary kafka & zookeeper logs (e.g. tmp/kafka-logs) and delete all data in this directory. Then start the kafka server`

## Test Topics
- Run command to verify if a topic was created: `.\bin\windows\kafka-topics.bat --describe --topic test_truong --bootstrap-server localhost:9092`
- Open terminal to create an event to the topic: `.\bin\windows\kafka-console-producer.bat --topic test_truong --bootstrap-server localhost:9092`
- Write some events into `test_truong` topic: **This is truong event**
- Open terminal to read the event from the topic: `.\bin\windows\kafka-console-consumer.bat --topic test_truong --from-beginning --bootstrap-server localhost:9092`
- Will see the events printed out from reading by the consumer **This is truong event**

# Kafka for MacOS
Same to commands with WinOS, but the relative path to `./bin/kafka-topics.sh`

# Misc
Happy coding!
