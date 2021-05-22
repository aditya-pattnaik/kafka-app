# Kafka Demo Application

## Producer Application
- This application is used to read a csv file and publish it to a Kafka topic.
- To create a topic: `bin/kafka-topics.sh --create --topic clickstream-topic --bootstrap-server localhost:9092`
- To consume a topic: `bin/kafka-console-consumer.sh --topic clickstream-topic --from-beginning --bootstrap-server localhost:9092`
- Build the JAR using mvn clean install and go to the target folder. Run `java -jar ProducerApplication-0.0.1-SNAPSHOT-jar-with-dependencies.jar /home/aditya/Downloads/ClickStreamMasterData.csv clickstream-topic`
- Here the first argument to java -jar app.jar is the csv file path and second argument is the topic name.
