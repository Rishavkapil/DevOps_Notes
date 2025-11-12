	

## Step 1 : To setup ELK Stack 

1. Clone the below repo : 

```
https://github.com/Rishavkapil/docker-ekl-setup.git
```

then  run `docker-compose up setup`

sometime the above step can take few minutes, 

after this, `docker-compose up -d`


After doing this, your elastic search and kibana will be running :

```

Elastic Search : 

http://localhost:9200

Kibana: 

http://localhost:5601
```


## Step 2 : Now you need to setup metricbeat to collect metrics. 

if you are on linux(ubuntu), then you can directly download it from the below link : 

```
curl -L -O https://artifacts.elastic.co/downloads/beats/metricbeat/metricbeat-8.18.8-linux-x86_64.tar.gz
tar xzvf metricbeat-8.18.8-linux-x86_64.tar.gz
```

or if you're using some other device. you can also download it from the following : 


```
https://www.elastic.co/guide/en/beats/metricbeat/8.18/metricbeat-installation-configuration.html
```


After downloading , go to the new directory 
then we need to change the configuration . 

```
vim metricbeat.yml

then you need to uncommnet this line : host: "localhost:5601"
```

and then also uncomment a line in `Elasticsearch output` section. 

```
username: "elastic"
password: "changeme"
```

then if you want to monitor docker container, then you need to enable the docker module of metricbeat. 
for that do 

```
./metricbeat modules enable docker
```

After docker is enabled you'll see a file inside modules.d folder , named docker.yml

Edit docker.yml file

```
uncomment metricsets and the mertics that you want to monitor
```

then go back to previous directory and run 

```
./metricbeat setup -e
```

this will load dashboards and other necessary things to kibana. 

then if you want to test , you can run `./metricbeat test config`

Then run `./metricbeat -e`

and then open kibana and then go to dashboards, and then search for docker , you'll see metricbeat giving docker containaer info. 


