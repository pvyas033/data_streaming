# **Data_streaming**

1. FluentD: We are configuring FluentD so it will forward messages from Kafka Broker to Newrelic Dashboard.

    You have to change below values in fluentd.conf
    
    ``brokers <KAFKA_BROKER_IP> (e.g. 10.190.1.1, kafka)``
   
    ``topics <TOPIC_NAME> (e.g. vyastopic)``
   
    ``format <FORMAT> (e.g. json)``
    
    ``@type newrelic``
   
    ``api_key <NEWRELIC_API_KEY>``
    
    Build fluentd image:
    
    ``docker build . -t fluentdpv``
    
2. Now run below command to up all three containers(zookeeper, kafka, fluentd)

   ``docker-compose up``


Below are the testing commands to check if the setup is working or not:

1. Download 'kafka_2.12-3.6.1.tgz' from [Apache Downloads](https://kafka.apache.org/downloads) (you can download latest version as well)
2. Navigate to '\kafka_2.12-3.6.1\bin\windows'.
3. To create kafka topic run below command:
   ``kafka-topics.bat --create --topic vyastopic --bootstrap-server localhost:9092``
4. To produce kafka messages run below command:
   ``kafka-console-producer --topic vyastopic --bootstrap-server localhost:9092``
5. For listening messages run below command:
   ``kafka-console-consumer.bat --bootstrap-server localhost:9092 --topic vyastopic --from-beginning``
   
