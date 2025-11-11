

### Prerequisites 
Your system should have atleast one container running in Docker to ship some useful data to Elastic Search and Kibana. 


## Install Metric Beat

To install metric beat, you first need to add Elastic's signing key used to verify the downloaded package: 

```
wget -qO - https://artifacts.elastic.co/GPG-KEY-elasticsearch | sudo apt-key add -

```

Next, add the Elastic repository to your repository source list: 

```
echo "deb https://artifacts.elastic.co/packages/6.x/apt stable main" | sudo tee -a /etc/apt/sources.list.d/elastic-6.x.list

```


Finally, update the repos on your system and install metric beat using apt-get 


```
sudo apt-get update && sudo apt-get install metricbeat
```

by default `metric.yml` is located at `/etc/metricbeat`


