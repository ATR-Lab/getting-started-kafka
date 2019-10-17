# Getting Started with Kafka
Getting started with Kafka. Instruction, tutorials, demos and reference.

## Table Contents

- [Dependencies](#dependencies)
- [Installation](#installation)



## Dependencies

In this tutorial we will be using Java, you will need to [Java](https://www.oracle.com/technetwork/java/javase/downloads/jdk13-downloads-5672538.html) on your machine.

You may following the [link] for the Java installation tutorial.


## Installation

You can download the latest version of Kafka from this [link](https://www.apache.org/dyn/closer.cgi?path=/kafka/2.3.0/kafka_2.11-2.3.0.tgz)


Once you've downlaoded the Kafka:

It is preferable to keep all the files related to Kafka together, hence make a directory first.

```
$ mkdir Kafka
```
Moving my Kafka files to Kafka folder

```
$ mv ~/Downloads/kafka_2.11-2.3.0 /Kafka
```

Uncompressing the file

```
$ tar -xvf kafka_2.11-2.3.0
```

To check if you Java is working properly enter the following code of line:

```
bin/kafka-topics.sh
```
It should return bunch of kafa topics related commands. If not Java is not installed and you may type the following command to do it:

```
sudo apt install openjdk-8-jdk
```

You can also add the path of binaries file in the kafka folder, which is convenient way of using Kafka without going into it's directory. You can do this by following:

```pwd```

```
export PATH=/*your pwd's result for working directory*/Kafka/bin:$Path
```
Now when you type ```kafka-topics.sh``` you should be able to see the options related to them. 

#### NOTE: It is recommended to keep separate locations for data for Zookeeper and the logs. 
Which is why we do the following:

- Create a folder under your Kafka directory name data and another directory in data, call it zookeeper

```
mkdir data

mkdir data/zookeeper
```

- Under your Kafka directory and look for a file named zookeeper.properties which should be under configurations folder(Kafka/config/zookeeper.properties)

```
dataDirs = /home/skywalker/Kafka/kafka_2.11-2.3.0/data/zookeeper

```

- Similarly for your Kafka logs(Kafka/config/server.properties), and look for log.dirs to your data/kafka, something like the following:

```
log.dirs=/home/skywalker//Kafka/kafka_2.11-2.3.0/data/kafka
```

To fire up the Kafka, following are the instructions:

- Run the following to start up with Zookeeper, 
```

zookeper-server-start.sh config/zookeeper.properties 

```

- Run the following for Kafka, it should be able to see KafkaServer id = 0 started message:

```
kafka-server-start.sh config/server.properties
```


With this we have completed installation process. 
