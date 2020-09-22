Kafka Installation Method:

Copy the kafka software which is placed in the shared path (Z:\GlossaryManagementTool\from JAPAN )
Unzip .tgz file of Kafka 
And again unzip .tar file and extract the file

How to test the Kafka setup?

Start the zookeeper server first:
kafka_2.11-2.0.0\bin\windows\zookeeper-server-start.bat  kafka_2.11-2.0.0\config\zookeeper.properties

Start the Kafka server:
kafka_2.11-2.0.0\bin\windows\kafka-server-start.bat  kafka_2.11-2.0.0\config\server.properties

If kafka server started successfully then verify this log in server log file
[KafkaServer id=0] started (kafka.server.KafkaServer)



Zookeeper:


Zookeeper is a distributed, open-source configuration and synchronization service.

Role of zookeeper in Apache Kafka:

1. Zookeeper manages brokers(keeps a list of them)
2. Zookeeper helps in performing leader elections for partitions. 
For instance, if a broker is down, zookeeper will help in selecting a new partition as a leader
3. zookeeper sends notifications to kafka in case of changes (e.g. new topic, broker dies, broker comes up, delete topics, etc..)
4. Kafka can't work without Zookeeper
5. Kafka manages metadata in zookeeper

How to start a zookeeper?

In windows:
kafka_2.11-2.0.0\bin\windows\zookeeper-server-start.bat  kafka_2.11-2.0.0\config\zookeeper.properties


Broker:


A Kafka broker is also known as Kafka server and a Kafka node.
Kafka broker is more precisely described as a Message Broker which is responsible for mediating the conversation between different computer systems, guaranteeing delivery of the message to the correct parties.

Purpose of Broker:
1. The Kafka cluster typically consists of multiple brokers(servers).
2. Each broker is identified with its ID(Integer)
3. Each Broker contains certain topic partitions and a single Broker can handle thousands of reads and writes per second.
4. Each Broker contains the metadata of the other brokers which are residing in the same cluster.

How to Start Kafka Broker?

We can start a Kafka server, only when Zookeeper is up and running(that will connect to Zookeeper).
In Windows:
kafka_2.11-2.0.0\bin\windows\kafka-server-start.bat  kafka_2.11-2.0.0\config\server.properties


Producer:

An application that is the source of the data stream is what we call a producer.
In order to generate messages and further publish it to one or more topics in the Kafka cluster, we use Apache Kafka Producer.

Purpose of Kafka Producer:

1. The producer sends data directly to the broker that is the leader for the partition.
2. Producers can choose to send a key with the message(a key can be a string, number, etc..)
	If key=null, data is sent round robin(the default partitioning strategy for producers).
3. Producers can choose to receive acknowledgement of data writes:
	acks=0: Producer wont wait for acknowledgement(possible data loss)
	acks=1: Producer will wait for leader acknowledgement(limited data loss)
	acks=all: Leader + replicas acknowledgement(no data loss)

How to produce a message ?
kafka_2.11-2.0.0\bin\windows\kafka-console-producer.bat --broker-list localhost:9093 --topic control-proto
proto001, 50



Consumer:

1. The Kafka consumer works by issuing "fetch" requests to the brokers leading the partitions it wants to consume
2. Consumers read data from a topic(identified by name)
3. Data is read in order within each partitions

How to consumer a message ?
kafka_2.11-2.0.0\bin\windows\kafka-console-consumer.bat --broker-list localhost:9093 --topic control-proto --from-beginning
proto001, 50


Producer Java Application:

1. To create messages, first, we need to configure a ProducerFactory which sets the strategy for creating Kafka Producer instances
2. Then we need a KafkaTemplate which wraps a Producer instance and provides convenience methods for sending messages to Kafka topics

Producer Configuration :

@Configuration
public class KafkaProducerConfig {
 
    @Bean
    public ProducerFactory<String, String> producerFactory() {
        Map<String, Object> configProps = new HashMap<>();
        configProps.put(
          ProducerConfig.BOOTSTRAP_SERVERS_CONFIG, 
          bootstrapAddress);
        configProps.put(
          ProducerConfig.KEY_SERIALIZER_CLASS_CONFIG, 
          StringSerializer.class);
        configProps.put(
          ProducerConfig.VALUE_SERIALIZER_CLASS_CONFIG, 
          StringSerializer.class);
        return new DefaultKafkaProducerFactory<>(configProps);
    }
 
    @Bean
    public KafkaTemplate<String, String> kafkaTemplate() {
        return new KafkaTemplate<>(producerFactory());
    }
}

Publishing Messages: 

@Autowired
private KafkaTemplate<String, String> kafkaTemplate;
 
public void sendMessage(String msg) {
    kafkaTemplate.send(topicName, msg);
}

Consumer Java Application:

1. For consuming messages, we need to configure a ConsumerFactory and a KafkaListenerContainerFactory.
2. Consumers can be configured using @KafkaListener annotation

3. @EnableKafka annotation is required on the configuration class to enable detection of @KafkaListener annotation on spring managed beans

Consumer Configuration:

@EnableKafka
@Configuration
public class KafkaConsumerConfig {
 
    @Bean
    public ConsumerFactory<String, String> consumerFactory() {
        Map<String, Object> props = new HashMap<>();
        props.put(
          ConsumerConfig.BOOTSTRAP_SERVERS_CONFIG, 
          bootstrapAddress);
        props.put(
          ConsumerConfig.GROUP_ID_CONFIG, 
          groupId);
        props.put(
          ConsumerConfig.KEY_DESERIALIZER_CLASS_CONFIG, 
          StringDeserializer.class);
        props.put(
          ConsumerConfig.VALUE_DESERIALIZER_CLASS_CONFIG, 
          StringDeserializer.class);
        return new DefaultKafkaConsumerFactory<>(props);
    }
 
    @Bean
    public ConcurrentKafkaListenerContainerFactory<String, String> 
      kafkaListenerContainerFactory() {
    
        ConcurrentKafkaListenerContainerFactory<String, String> factory
          = new ConcurrentKafkaListenerContainerFactory<>();
        factory.setConsumerFactory(consumerFactory());
        return factory;
    }
}


Consuming Messages:

@KafkaListener(topics = "topicName")
public void listen(String message) {
    System.out.println("Received Message: " + message);
}

SSL in Kafka:
 SSL is secure socket layer which is predominantly referred to TLS(Transport Level Security) in the IT.

1. Encryption of data while transmission through netword using SSL / TLS. This allows your data to be encrypted between producers and Kafka and consumers and Kafka
2. SSL can be configured for both encryption or authentication.
3. SSL encryption enables 1-way authentication in which the client authenticates the server certificate and solves the problem of the man in the middle (MITM) attack
4. SSL authentication which is referring to 2-way authentication in which the broker also authenticates the client certificate 
5. SSL uses private-key/certificates pairs which are used during the SSL handshake process.
	a) each broker needs its own private-key/certificate pair, and the client uses the certificate to authenticate the broker
	b) each logical client needs a private-key/certificate pair if client authentication is enabled, and the broker uses the certificate to authenticate the client
6. With SSL, only the first and the final machine possess the ability to decrypt the packet(data) being sent.	
7. Enabling SSL may have a performance impact due to encryption overhead.

How to configure SSL in Kafka?

We have already configured the SSL and placed the setup process document in the project repository
control-proto/commandLine/KafkaSSLConfiguration.txt




Partitions:

Before describing about the partitions, we need to discuss about the "What is a topic"

Topic:
1. Topics is a particular stream of data
2. It is similar to table in  a database(without all constraints)
3. A topic is defined by it's name

4. Topics are split into partitions to provide parallelism while storing the messages
5. Each partition is ordered.
6. Each message within a partition gets an incremental id, called an offset
7. We can assign the total no.of partitions while creating a topic
8. We can alter the existing topic with the desired no. of partitions at any time

//Topic creation with 1 partition

```
bin\windows\kafka-topics.bat --create --zookeeper localhost:9002 --replication-factor 1 --partitions 1 --topic user-cache 
```

//Alter topic with 4 partitions
```
bin\windows\kafka-topics.bat --zookeeper localhost:2181 --alter --topic user-cache --partitions 4
```


38c8d69f-b080-4d19-855e-40bd9759de6e


