# Data_streaming

1. FluentD: We are configuring FluentD so it will forward messages from Kafka Broker to Newrelic Dashboard.

    You have to change below values in fluentd.conf
    
    ``brokers <KAFKA_BROKER_IP> (e.g. 10.190.1.1)``
   
    ``topics <TOPIC_NAME> (e.g. testtopic)``
   
    ``format <FORMAT> (e.g. json)``
    
    ``@type newrelic``
    ``api_key <NEWRELIC_API_KEY>``
    
    Build fluentd image:
    
    ``docker build . -t fluentdpv``
    
    Then Run below command to run Fluentd server
    
    ``docker run -d --name pvfluentd -p 24224:24224 fluentdpv``
    
    Now kafka messages will transfer from kafka via fluentd to Newrelic.
