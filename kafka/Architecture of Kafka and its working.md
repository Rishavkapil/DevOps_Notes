To understand kafka better, let's take an example of amazon. When we purchase any product from amazon we need every notification in real time basis. 

Rabbitmq does the same thing but it fails to handle large data. 


Apache kafka has 3 main components : 

* Producer
* Consumer
* Broker

### Producers

Producers are source of data pushing records into the kafka topics. For example, when you like something on instagram , all of these things are considered as producer. Because data is getting generated. 


### Consumers

Consumers are the people who consume this data to do something about this. 

So In this case, if you're a data engineer, you will consume this data, process as per business requirements and publish this to data warehouse or other data storage system. 


Now we can publish and consume data using kafka topics .

**Topics** are basically categories or feed names. 

eg. In amazon we can create multiple topics, one topic for ordering, one for returning, one for payments, one for shipping etc.  All of these are different categories of topics that we can create to separate our data logically. 

We can create different partitions inside a topic. eg. data or region. 


Producers can publish data to a topic and consumer can subscribe to that topic. 

In this architecture , we also have broker & cluster. A kafka broker is a server that store data and serves client requests. It can be an ec2 instance , you can consider it as a server or broker and the combination of these multiple machines can be considered as a cluster. 

Each record in the partition is immutable . 

Each record in the partition has an offset , which basically means position of the particular record inside the partition. (offset = id/index)


For more , Please refer to this blog post on medium : https://medium.com/swlh/apache-kafka-what-is-and-how-it-works-e176ab31fcd5

