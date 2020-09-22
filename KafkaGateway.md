A plugin interface that allows us to intercept (and possibly mutate) records received by the consumer. 
A primary use-case is for third-party components to hook into the consumer applications for custom monitoring, logging, etc

In control-proto project we have utilised the Kafka's ConsumerInterceptor API(Interface) which is inherited from Configurable

We have declared a class called KafkaInterceptor which implements the ConsumerInterceptor<String, Object> and overrides the methods present in the API

ConsumerInterceptor<K, V> 

A plugin interface to allow things to intercept Consumer events such as receiving a record or record being consumed by a client.

Configuration:

Add a new configuration setting KafkaInterceptor.class to the KafkaConsumer API which is then used as consumer interceptors.
 
KafkaInterceptor class must implement ConsumerInterceptor interface.

configuration as follows:

Step 1:

Add the below line of code to the consumerFactory() in the KafkaConfig class
 
props.put(ConsumerConfig.INTERCEPTOR_CLASSES_CONFIG, KafkaInterceptor.class.getName());

Step 2:

Configure the KafkaInterceptor class in classpath i.e.. application-dev.yml

Spring:
  kafka:
    consumer:
      properties:
        interceptor:
          classes: com.fujitsu.interceptors.KafkaInterceptor
		  
Methods description:

Method 1:
configure() :

/**
* @param configs is a map object and contains the kafka consumer configuration properties such as SSL protocol, groupID, auto commit etc
*/

```java
@Override
	public void configure(Map<String, ?> configs) {

		logger.debug("\n-------- Log Interception while configure --- \"");
		
		configs.forEach((k,v) -> System.out.println("Item ------------>  : " + k + " Count ------>: " + v));
	}
```
Method 2:

onConsume() :

This method will be called in KafkaConsumer.poll(), just before poll() returns ConsumerRecords. 
The implementation of onConsume() is allowed to read key and values in ConsumerRecords and save them into the log.
In the below code, we are differentiating each record being consumed based on uniqueID and timeStamp
and saving the following information to the log --> Topic name, Topic partition, offset of the partition being consumed etc
 
```java
@Override
	public ConsumerRecords<String, String> onConsume(ConsumerRecords<String, String> records) {

		uniqueID = UUID.randomUUID().toString();
		startTime = new Timestamp(System.currentTimeMillis());

		uniqueTimeAndIdThread.set(new UniqueIDAndTimestamp(uniqueID, startTime));

		for (ConsumerRecord<String, String> record : records) {

			logger.debug("\n-------- Log Interception while onConsume --- \"");

			logger.debug("topic name of the record being processed--->" + record.topic());

			logger.debug("Partition from which the record is being consumed --->" + record.partition());

			logger.debug("the offset being pointed to the record in a Kafka partition --->" + record.offset());

			logger.debug("The key of the record --->" + record.key());

			logger.debug("Content of the record being processed--->" + record.value());

			logger.debug("The timestamp  @ onConsume stage --> " + uniqueTimeAndIdThread.get().getStartTime());

			logger.debug("The unique Id for the uniqueIdThread  while onConsume --> "
					+ uniqueTimeAndIdThread.get().getUniqueID());
		}

		logger.debug("records count onConsume --->" + records.count());
		
		return records;

	}

```	
Method 3:

onCommit() :

/**
     * This is called when offsets get committed
     * This method will be called when the commit request sent to the server has been acknowledged.
     * @param offsets A map of the offsets and associated metadata that this callback applies to
     */

```java
@Override
	public void onCommit(Map<TopicPartition, OffsetAndMetadata> offsets) {

		logger.debug("\n-------- Log Interception while onCommit --- \"");

		logger.debug("\n-------- onCommit offset values" + offsets.values());

	}
```
Method 4:

close() :

/**
     * This is called when interceptor is closed
     */
```java  
  public void close() {

		logger.debug("\n-------- Log Interception on close --- \"");

	}
```	

The complete code sample as follows:

```java	
public class KafkaInterceptor implements ConsumerInterceptor<String, String> {

	private static final Logger logger = LoggerFactory.getLogger(KafkaInterceptor.class);

	String uniqueID;
	Timestamp startTime;

	ThreadLocal<UniqueIDAndTimestamp> uniqueTimeAndIdThread = new ThreadLocal<>();

	@Override
	public void configure(Map<String, ?> configs) {

		logger.debug("\n-------- Log Interception while configure --- \"");
		
		configs.forEach((k,v) -> System.out.println("Item ------------>  : " + k + " Count ------>: " + v));
		

	}

	@Override
	public ConsumerRecords<String, String> onConsume(ConsumerRecords<String, String> records) {

		uniqueID = UUID.randomUUID().toString();
		startTime = new Timestamp(System.currentTimeMillis());

		uniqueTimeAndIdThread.set(new UniqueIDAndTimestamp(uniqueID, startTime));

		for (ConsumerRecord<String, String> record : records) {

			logger.debug("\n-------- Log Interception while onConsume --- \"");

			logger.debug("topic name of the record being processed--->" + record.topic());

			logger.debug("Partition from which the record is being consumed --->" + record.partition());

			logger.debug("the offset being pointed to the record in a Kafka partition --->" + record.offset());

			logger.debug("The key of the record --->" + record.key());

			logger.debug("Content of the record being processed--->" + record.value());

			logger.debug("The timestamp  @ onConsume stage --> " + uniqueTimeAndIdThread.get().getStartTime());

			logger.debug("The unique Id for the uniqueIdThread  while onConsume --> "
					+ uniqueTimeAndIdThread.get().getUniqueID());
		}

		logger.debug("records count onConsume --->" + records.count());
		
		return records;

	}

	@Override
	public void onCommit(Map<TopicPartition, OffsetAndMetadata> offsets) {

		logger.debug("\n-------- Log Interception while onCommit --- \"");

		logger.debug("\n-------- onCommit offset values" + offsets.values());

	}

	@Override
	public void close() {

		logger.debug("\n-------- Log Interception on close --- \"");

	}

}
```