## Kafka on MAC
Kafka installation is done after installing everything described in README.md.

Download the followings:
* [Apache ZooKeeper 3.6.2](https://www.apache.org/dyn/closer.lua/zookeeper/zookeeper-3.6.2/apache-zookeeper-3.6.2-bin.tar.gz)
* [kafka-2.4.1](https://www.apache.org/dyn/closer.cgi?path=/kafka/2.4.1/kafka_2.11-2.4.1.tgz) (scala v2.11)

Extract the files under:
/Users/lisan/server/

Add the following to .bash_profile: 
export PATH="$PATH:/Users/lisan/server/kafka_2.11-2.4.1/bin"
export PATH="$PATH:/Users/lisan/server/apache-zookeeper-3.6.2-bin/bin"

#### Configuring zookeeper  
$ vi /Users/lisan/server/apache-zookeeper-3.6.2-bin/conf/zoo.cfg  
tickTime=2000 initLimit=10 syncLimit=5  
dataDir=/Users/lisan/server/apache-zookeeper-3.6.2-bin/data  
clientPort=2181

#### Starting zookeeper server:  
$ zkServer.sh start  

#### Starting kafka server:  
$ kafka-server-start.sh ./config/server.properties  

#### Creating kafka topic:  
$ kafka-topics.sh --create --zookeeper localhost:2181 
--replication-factor 1 --partitions 1 --topic test

kafka-topics.sh --create --zookeeper localhost:2181 --replication-factor
1 --partitions 1 --topic data-topic1  

Checking list of Kafka topics:  
$ kafka-topics.sh --list --zookeeper localhost:2181

#### Run the producer:  
$ kafka-console-producer.sh --broker-list localhost:9092 --topic test

#### Run the consumer:  
$ kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic
test --from-beginning

#### Stopping zooker server:  
$ zkServer.sh stop


