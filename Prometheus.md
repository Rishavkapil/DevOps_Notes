			
**Prometheus** is an open-source monitoring and alerting system used for event monitoring and alerting. 

used for monitoring and collecting application metrics.

**Metrics** are numerical measurements . These are collected from applications or infrastructure and stored in time-series database for querying and alerting. 

The time series refers to the recording of changes over time. 

Metrics play an important role in understanding why your application is running in a certain way. 

It is metrics based monitoring system that helps you ensure that your system and services are healthy and behaving well. 

It uses a Pull-based model , where it scrapes metrics from configured endpoints at regular intervals and store them in a time-series database. 


Users can query the collected data with the help of PromQL(Prometheus Query Language) to analyze the system performance , generate alerts , and visualize trends. 



#### Why do we need Prometheus ?


* Real Time Monitoring 
* Scalability 
* Alerting System


#### Architecture 

The below diagram illustrate the architecture of Prometheus and some of its ecosystem components : 

![[Pasted image 20250320174533.png]]


The Prometheus server pulls metrics from the application (jobs/exporters) it can be anything like kubernetes , Docker Containers etc. 


then it stores that metrics in Time-series Database . 
then it gives that metrics to grafana through promtail and then grafana visualizes it . 

Alert managers can also be attached to the Prometheus server which is used to send alerts like if CPU usage reaches 85% then send alert to user through email . 

Loki can also be attached to the Prometheus server which shows the logs . 




### How does Prometheus Work 

1. **Data Collection and retrieval :** 
	Prometheus follows a pull-based model , where it periodically scrapes data from the targets that are instrumented with its client libraries. 

2. **Data Storage :** 
	The collected metrics are stored in time-series database, providing a historical record of system performance overtime. 

3. **Service Discovery :** 
	Prometheus utilizes discovery mechanism to ensure that new instance are automatically deleted and monitor without manual intervention. 




#### What is Node Exporter ?

The Prometheus Node exporter is an open-source time-series monitoring and alerting system for cloud-native environments , including kubernetes , hosted by Cloud Native Computing Foundation (CNCF) on Github. 