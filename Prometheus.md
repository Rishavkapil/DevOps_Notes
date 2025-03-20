
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

