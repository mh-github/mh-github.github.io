## Configuring Apache Kafka MongoSinkConnector on Windows

I downloaded the connector from [confluent](https://www.confluent.io/hub/mongodb/kafka-connect-mongodb)
<br/>
Click on the blue Download button at the left to get **mongodb-kafka-connect-mongodb-1.0.1.zip** file.

<br/>
There is an -all.jar file in the zip. There is also the file **MongoSinkConnector.properties** in the etc folder inside the zip file.

<br/>
My Kafka installation folder is E:\Tools\kafka_2.12-2.4.0
Move the jar file to kafka_installation_folder\\**plugins**.
Move the properties file to kafka_installation_folder\\**config**.

<br/>
That is, in my case,
<br/>E:\Tools\kafka_2.12-2.4.0\\**plugins** has **mongo-kafka-1.0.1-all.jar** file. And E:\Tools\kafka_2.12-2.4.0\\**config** has **MongoSinkConnector.properties**.


My **connect-standalone.properties** file has the following entries:
```
bootstrap.servers=localhost:9092
key.converter=org.apache.kafka.connect.json.JsonConverter
value.converter=org.apache.kafka.connect.json.JsonConverter

key.converter.schemas.enable=false
value.converter.schemas.enable=false

offset.storage.file.filename=/tmp/connect.offsets
offset.flush.interval.ms=10000
plugin.path=E:/Tools/kafka_2.12-2.4.0/plugins/mongo-kafka-1.0.1-all.jar
```

My **MongoSinkConnector.properties** file has the following entries
```
name=mongo-sink
topics=topic1,topic2
connector.class=com.mongodb.kafka.connect.MongoSinkConnector
tasks.max=1

connection.uri=mongodb://localhost:27017,localhost:27017,localhost:27017
database=test_kafka
collection=transactions
max.num.retries=3
retries.defer.timeout=5000

field.renamer.mapping=[]
field.renamer.regex=[]

max.batch.size = 0
rate.limiting.timeout=0
rate.limiting.every.n=0
```

**How To Run**

Start mongodb, zookeeper, kafka server in three consoles.

In 4th console, start Kafka connect --

`bin\windows\connect-standalone config\connect-standalone.properties config\MongoSinkConnector.properties`

In 5th console, send msgs to a topic (I did for topic1)
`bin\windows\kafka-console-producer --broker-list localhost:9092 --topic topic1`
<br/>\>{"Hello":1}
<br/>\>{"Mongo":2}
<br/>\>{"World":3}

Open mongo (client) in a new (5th console) and check your database/collections.
You will see these three messages.
