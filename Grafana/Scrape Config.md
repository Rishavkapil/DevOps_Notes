
Scrape config is a configuration used to define how Prometheus collects metrics from various sources. 
Grafana itself doesn't perform scrapping , but it visualizes the data collected by Prometheus, which uses scrape configs to gather metrics. 

This is how scrape config works in context of Prometheus: 

* Scrape config define the targets from which Prometheus should collect data. 
* This configuration specifies details like the target's URL, the scrape interval , and whether the target should be scraped in a specific way .


eg. 


		scrape_configs:
		  - job_name: 'node'
		    static_configs:
		      - targets: ['localhost:9100']
	