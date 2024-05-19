
# Apache Kafka Docker Commands

### Run Docker Compose:

Open a terminal in the directory where the docker-compose.yml file is located and run the following command to start the Kafka and Zookeeper containers:

    docker-compose up -d

This command will download the required Docker images and start the Kafka and Zookeeper services in detached mode (-d).


### Verify Kafka Container is Running:

Check if the Kafka container is running by executing the following command:
    
    docker ps

You should see containers for both Kafka and Zookeeper in the list.


### Create a Kafka Topic

Create a Kafka topic using the following command:

    docker exec -it <kafka-container-id> /opt/kafka/bin/kafka-topics.sh --create --zookeeper zookeeper:2181 --replication-factor 1 --partitions 1 --topic <topic-name>

### Produce and Consume Messages

Use the Kafka console producer and consumer to test your Kafka setup:

#### Produce messages:

        docker exec -it <kafka-container-id> /opt/kafka/bin/kafka-console-producer.sh --broker-list localhost:9092 --topic <topic-name>

#### Consume messages:

        docker exec -it b2832daa6fe9 /opt/kafka/bin/kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic <topic-name> --from-beginning

### Stop and Remove Containers

To stop and remove the Kafka and Zookeeper containers, run:
        
        docker-compose down

