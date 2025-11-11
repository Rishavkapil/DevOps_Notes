
1. **Metrics (CPU, memory) :** Metric beat is used to collect docker container logs and metrics. 
		`Metricbeat  --> Elastic Search --> Kibana`
2. **Logs(Container stdout/stderr) :** Filebeat reads the docker log files  and ships logs. 
		`filebeat --> Elastic Search --> Kibana`
3. **Where to run beats :** on the host as a service or containers. If you run metric beat/filebeat  as container you must mount the docker socket + required host paths so the beat can query Docker and the host. 
