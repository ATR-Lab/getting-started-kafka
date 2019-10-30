# Getting Started with Kafka
Getting started with Kafka. Instruction, tutorials, demos and reference. In this tutorial we will look at the foundations of the Kafka.

## Table Contents
- [References](#references)
- [Dependencies](#dependencies)
- [Installation](#installation)


## References

Before getting started, this tutorial expects for you to have foundations and basic understanding of Kafka. Following are two resources(official documentation and notes) which can be used as a reference:

- The Kafka's [official documentation](https://kafka.apache.org/documentation/)

- [Google Doc](https://docs.google.com/document/d/14y4t6O9mbYQwFcNmw3bg_bvxtcLQsa9wfFJLVqAZ_VU/edit?usp=sharing), the link is for google document, you may comment on it in case if something is missing or you may want to provide more information.


## Dependencies

In this tutorial we will be using Java, you will need to [Java](https://www.oracle.com/technetwork/java/javase/downloads/jdk13-downloads-5672538.html) on your machine.

In case if you plan to work with Java, you may follow the [link] for the Java installation tutorial.

## Installation

This tutorial is explicitly worked with Ubuntu 18.04 

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
It should return bunch of kafa topics related commands. If not Java is not installed and you may type the following command to do it (if you plan to work with Java):

```
sudo apt install openjdk-8-jdk
```

If you decided to work with Python, you may install the Kafka package

```
pip install kafka-python
```


You can also add the path of binaries file in the kafka folder, which is convenient way of using Kafka without going into it's directory. You can do this by following:

```$ pwd```

```
export PATH=/*your pwd's result for working directory*/Kafka/bin:$Path
```
Now when you type ```kafka-topics.sh``` you should be able to see the options related to them. 

#### NOTE: It is recommended to keep separate locations for data for Zookeeper and the logs. 
Which is why we do the following:

- Create a folder under your Kafka directory name data and another directory in data, call it zookeeper 

```
$ mkdir data

$ mkdir data/zookeeper
```

- Under your Kafka directory and look for a file named zookeeper.properties which should be under configurations folder(Kafka/config/zookeeper.properties)

```
dataDirs = /home/skywalker/Kafka/kafka_2.11-2.3.0/data/zookeeper

```

Create a directory in data call it kafka

```
$ mkdir data/kafka
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

### Why do we need zookeeper?

Kafka's jobs are scheduled with the help of Zookeeper, in order Kafka to run, Zookeeper should be launched first.

### What is the importance of the topic? Can we have multiple topics?

Kafka topics are the primary place where the data is written into and read from. A topic can be used for keeping track of particular data. Let us consider there are dozens of trucks, for certain distance, the drivers of those trucks need to take a rest. You do this by tracking the their GPS which could be kept track of using topics.


### What is the significance of producer and consumer?

The Producer is one that sends the data or fair enough to say you they produce the data(I like to think it this way) and consumer is where the data is sent to. A key note to remember, your producer can be consumer too.
