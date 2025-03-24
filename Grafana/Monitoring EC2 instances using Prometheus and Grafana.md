
***Prerequisite:***
Launching 3 AMAZON Linux instances

Prometheus EC2 instance t2.micro
Node EC2 instances to monitor
Security Groups Configured properly
Clone this git repo

	https://github.com/Phanindra-Sangers/prometheus-monitoring.git

1. On One instance you need to setup Prometheus 
2. On 2nd instance you need to setup Node_exporter
3. On 3rd instance you need to setup Grafana


### Step 1 : Installing Prometheus 

launch once of the Instance and name it as prometheus Instance or as per your naming
	`$ sudo yum install git
	
	$ git clone https://github.com/Phanindra-Sangers/prometheus-monitoring.git

`
		`cd prometheus-monitoring`

			./install-promethues.sh


This script will install everything and configured it. You can change the version as per your project.


Script will do the following in the instance

Creates a new user and add new directories


### Step 3 :  Now we will configure Prometheus to monitor itself using yaml file.

Create a `prometheus.yml` file at `/etc/prometheus/prometheus.yml` with the below content

		$ cd /etc/prometheus

		
		$ vi prometheus.yml

Copy and paste following content in yml file opened 

                            global:
                              scrape_interval: 15s
                              external_labels:
                                monitor: 'prometheus'
                            
                            scrape_configs:
                              - job_name: 'prometheus'
                                static_configs:
                                  - targets: ['localhost:9090']



**Now we want to run the Prometheus as a Service so that in case of server restart service will come automatically**


create a file at

				$ cd /etc/systemd/system/


					$ vi prometheus.service



	## copy and paste the below content in the service file 

                    [Unit]
                    Description=Prometheus
                    Wants=network-online.target
                    After=network-online.target
                    
                    [Service]
                    User=prometheus
                    Group=prometheus
                    Type=simple
                    ExecStart=/usr/local/bin/prometheus \
                        --config.file /etc/prometheus/prometheus.yml \
                        --storage.tsdb.path /var/lib/prometheus/ \
                        --web.console.templates=/etc/prometheus/consoles \
                        --web.console.libraries=/etc/prometheus/console_libraries
                    
                    [Install]
                    WantedBy=multi-user.target




Change the ownership of all folders and files which we have created to the user which we have created in the first step



	sudo chown prometheus:prometheus /etc/prometheus
	sudo chown prometheus:prometheus /usr/local/bin/prometheus
	sudo chown prometheus:prometheus /usr/local/bin/promtool
	sudo chown -R prometheus:prometheus /etc/prometheus/consoles
	sudo chown -R prometheus:prometheus /etc/prometheus/console_libraries
	sudo chown -R prometheus:prometheus /var/lib/prometheus

Now we will configure the service and start it


	sudo systemctl daemon-reload
	sudo systemctl enable prometheus
	sudo systemctl start prometheus
	sudo systemctl status prometheus

now you can access the prometheus dashboard

$ [http://public-ip/9090](http://public-ip/9090)



![[Pasted image 20250324123904.png]]

![[Pasted image 20250324124342.png]]



#### Step 2 : Install the node exporter


Open AWS Console and create new instance as we informed at starting of the blog and name it is as Node exporter instance

install git

		$ sudo yum install -y git
	$ git clone [https://github.com/Phanindra-Sangers/prometheus-monitoring.git](https://github.com/Phanindra-Sangers/prometheus-monitoring.git)



Now to monitor your servers you need to install the node exporter on all your target machine which is like a monitoring agent on all the servers.

You can clone repo mentioned at starting of the blog and run it directly using below command

		cd prometheus-monitoring/

		$ ./install-node-exporter.sh


This script will do the below steps:



	sudo useradd --no-create-home node_exporter
	
	wget https://github.com/prometheus/node_exporter/releases/download/v1.0.1/node_exporter-1.0.1.linux-amd64.tar.gz
	tar xzf node_exporter-1.0.1.linux-amd64.tar.gz
	sudo cp node_exporter-1.0.1.linux-amd64/node_exporter /usr/local/bin/node_exporter
	rm -rf node_exporter-1.0.1.linux-amd64.tar.gz node_exporter-1.0.1.linux-amd64
	
	sudo cp node-exporter.service /etc/systemd/system/node-exporter.service
	
	sudo systemctl daemon-reload
	sudo systemctl enable node-exporter
	sudo systemctl start node-exporter
	sudo systemctl status node-exporter




It will create a new user , download the software using `wget` and then run the node-exporter as a service

Access the Node Exporter using

$ [http://public-ip:9100](http://public-ip:9100/)



![[Pasted image 20250324124650.png]]


####  Step 3 : Configure Prometheus for the Nodes

Now we will configure the Prometheus for our EC2 instance where we have installed the node-exporter.

Login to the Prometheus server and edit the file file at location in Prometheus instance

`/etc/prometheus/prometheus.yml`



					global:
					  scrape_interval: 15s
					  external_labels:
					    monitor: 'prometheus'
					
					scrape_configs:
					
					  - job_name: 'node_exporter'
					
					    static_configs:
					
					      - targets: ['18.219.214.162:9100']
					      - targets: ['7.4.5.6:9100']



Restart the Prometheus Service

			
					sudo systemctl restart prometheus
					sudo systemctl status prometheus


Now you can open the Prometheus using below url and can see the new targets added



		http://public-ip-of-prometheus-instance/9090/targets



![[Pasted image 20250324124918.png]]






### Step 4 : Install Grafana


install git in grafana instance

1. clone git repo

[https://github.com/Phanindra-Sangers/prometheus-monitoring.git](https://github.com/Phanindra-Sangers/prometheus-monitoring.git)

1. Run the below file for apt-get pckg manager

				./install-grafana.sh
				
				this script contains 
				
				sudo apt-get install -y adduser libfontconfig1
				wget https://dl.grafana.com/oss/release/grafana_7.3.4_amd64.deb
				sudo dpkg -i grafana_7.3.4_amd64.deb
				sudo systemctl daemon-reload
				sudo systemctl start grafana-server
				sudo systemctl status grafana-server
				sudo systemctl enable grafana-server.service



2. for YUM package manager

				wget https://dl.grafana.com/enterprise/release/grafana-enterprise-9.4.3-1.x86_64.rpm
				
				sudo yum install grafana-enterprise-9.4.3-1.x86_64.rpm




				
				sudo systemctl daemon-reload
				sudo systemctl start grafana-server
				sudo systemctl status grafana-server
				sudo systemctl enable grafana-server.service

Now open it on the browser using below url:

Make sure that port `3000` is open for this instance.


				
				http://yourip:3000


Login with username : `admin` and password `admin`


![[Pasted image 20250324125146.png]]



![[Pasted image 20250324125156.png]]\



Add Prometheus DataSource

Click on Setting ->datasources

add datasources



![[Pasted image 20250324125214.png]]



click on Prometheus


![[Pasted image 20250324125228.png]]



![[Pasted image 20250324125244.png]]




mention your prometheus IP

scroll down save and test



![[Pasted image 20250324125300.png]]


![[Pasted image 20250324125312.png]]



Click on Explore highlighted in red -> Select `Prometheus` as a datasource as shown below


![[Pasted image 20250324125709.png]]



ow you can click on metrics -> Select Up

Output `1` shows that the node is up

CLick on Run Query

you will get dashboards


![[Pasted image 20250324125725.png]]


Grafana provides lot of dashboards which we can directly import in our Grafana instance and use it.

In this example, we will use [this](https://grafana.com/grafana/dashboards?collector=nodeExporter&dataSource=prometheus&orderBy=downloads&direction=desc) dashboard

##### Import the dashboard

Click on `+` icon -> Import

![[Pasted image 20250324125813.png]]

![[Pasted image 20250324125827.png]]



select load — import — select the node to configured


![[Pasted image 20250324125848.png]]






***for more you can follow this blog on medium :*** 

	https://medium.com/@phanindra.sangers/monitoring-ec2-instance-using-prometheus-and-grafana-767aea3bbf14