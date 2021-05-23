# Kafka Demo Application

## Producer Application
- Read a csv file and publish it to a Kafka topic using KafkaProducer API. 
- To create a topic: `bin/kafka-topics.sh --create --topic clickstream-topic --bootstrap-server localhost:9092`
- To consume a topic: `bin/kafka-console-consumer.sh --topic clickstream-topic --from-beginning --bootstrap-server localhost:9092`
- Build the JAR using mvn clean assembly:single and go to the target folder. Run `java -jar ProducerApplication-0.0.1-SNAPSHOT-jar-with-dependencies.jar /home/aditya/Downloads/ClickStreamMasterData.csv clickstream-topic`
- Here the first argument to java -jar app.jar is the csv file path and second argument is the topic name.

## Stream Application
- Read the messages from a Kafka topic as a stream, filter the records and ingest filtered record to a new topic using KafkaStreams API.
- To create new topic: `bin/kafka-topics.sh --create --topic cleansed-clickstream-topic --bootstrap-server localhost:9092`
- To consume new topic: `bin/kafka-console-consumer.sh --topic cleansed-clickstream-topic --from-beginning --bootstrap-server localhost:9092`
- Build the JAR using mvn clean assembly:single and go to the target folder. Run `java -jar StreamApplication-0.0.1-SNAPSHOT-jar-with-dependencies.jar clickstream-topic cleansed-clickstream-topic`
- Here the first argument to java -jar app.jar is the old topic name and second argument is the new topic name.

## Consumer Application
- Subscribe and consume from the cleansed-clickstream-topic and Print the metadata along with the actual messages.
- Build the JAR using mvn clean assembly:single and go to the target folder. Run `java -jar ConsumerApplication-0.0.1-SNAPSHOT-jar-with-dependencies.jar`
- Output:
  ```Consumer Record: Key - Cust069 Value - Cust069,2014-04-06T18:44:58.314Z,PROD001$PROD021$PROD011,192.18.12.4,150,http://YouBuyy.com/Mob1 Partition - 0 Offset - 71562
  Consumer Record: Key - Cust070 Value - Cust070,2014-04-06T18:44:58.314Z,PROD001$PROD002$PROD011,192.18.12.5,150,http://YouBuyy.com/Mob1 Partition - 0 Offset - 71563
  Consumer Record: Key - Cust071 Value - Cust071,2014-04-06T18:44:58.314Z,PROD001$PROD021$PROD011,192.18.12.6,150,http://YouBuyy.com/Mob1 Partition - 0 Offset - 71564
  Consumer Record: Key - Cust072 Value - Cust072,2014-04-06T18:44:58.314Z,PROD001$PROD021$PROD011,192.18.12.7,150,http://YouBuyy.com/Mob1 Partition - 0 Offset - 71565
  Consumer Record: Key - Cust073 Value - Cust073,2014-04-06T18:44:58.314Z,PROD001$PROD021$PROD011,192.18.12.8,150,http://YouBuyy.com/Mob1 Partition - 0 Offset -  71566```

## Kafka Architecture

![k3](https://user-images.githubusercontent.com/49421121/119250679-5d190300-bbbf-11eb-997c-5d8ffd86ae92.png)
