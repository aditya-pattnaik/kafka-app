# Kafka Demo Application

## Producer Application
- Read a csv file and publish it to a Kafka topic using KafkaProducer API. 
- To create a topic: `bin/kafka-topics.sh --create --topic clickstream-topic --bootstrap-server localhost:9092`
- To consume a topic: `bin/kafka-console-consumer.sh --topic clickstream-topic --from-beginning --bootstrap-server localhost:9092`
- Build the JAR using mvn clean install and go to the target folder. Run `java -jar ProducerApplication-0.0.1-SNAPSHOT-jar-with-dependencies.jar /home/aditya/Downloads/ClickStreamMasterData.csv clickstream-topic`
- Here the first argument to java -jar app.jar is the csv file path and second argument is the topic name.

## Stream Application
- Read the messages from a Kafka topic as a stream, filter the records and ingest filtered record to a new topic using KafkaStreams API.
- To create new topic: `bin/kafka-topics.sh --create --topic cleansed-clickstream-topic --bootstrap-server localhost:9092`
- To consume new topic: `bin/kafka-console-consumer.sh --topic cleansed-clickstream-topic --from-beginning --bootstrap-server localhost:9092`
- Build the JAR using mvn clean install and go to the target folder. Run `java -jar StreamApplication-0.0.1-SNAPSHOT-jar-with-dependencies.jar clickstream-topic cleansed-clickstream-topic`
- Here the first argument to java -jar app.jar is the old topic name and second argument is the new topic name.
