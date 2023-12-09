# Data_streaming

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
