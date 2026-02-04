
Loki is a log aggregation system developed by Grafana Labs, designed to store and query logs from all your applications and infrastructure . 

Loki is a horizontally scalable, highly available , multi tenant-log aggeregation system . 

It is designed to be very cost-effective and easy to operate. 

It does not index the content of the logs , but rather set a labels for each log stream . 


**To collect logs and view your data generally involves the following steps:** 
![[Pasted image 20250326150405.png]]

Loki does not index the entire log contents. Instead it indexes metadata and stores logs as compressed chunks , making it more cost-effective and scalable . 


### Key Features of Loki 

1. **Label-based indexing :** Instead of indexing full logs, **loki** organizes logs using labels. 
2. **Efficient Storage :** Stores logs in chunks   
3. **Integration with Grafana :** Loki is seamlessly integrated with grafana for visualization . 
4. **LogQL(Loki query Language) :** A powerful query language for filtering and searching logs. 
5. **Multi-Tenant support :** Can handle logs from multiple sources while keeping them isolated. 
6. **Pull-based Model :** Loki supports pull-based models using Promtail, Fluentd or other log shippers. 



## Loki Components 

**Loki :** The main log database that store logs. 
**Promtail :** A log shipper that collects and forwards logs to loki. 
**Grafana :**  Used to visualize and analyze logs. 
**LogCLI :** A Command line tool to query logs. 



We can store the logs of **LOKI** either in local system or in S3 Bucket. 

![[Pasted image 20250326171435.png]]


