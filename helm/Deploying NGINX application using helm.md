


## Step 1 : Create helm chart

			helm create nginx-nodeport
		

this will create the structure : 

			nginx-nodeport/
			├── charts/
			├── templates/
			├── values.yaml
			└── ...



# Helm chart : Folder and file structure 


### chart.yml

This is the metadata file of your helm chart . 

			apiVersion: v2
			name: nginx-nodeport
			description: A Helm chart for Kubernetes
			type: application
			version: 0.1.0
			appVersion: "1.16.0"



### values.yml

				replicaCount: 1
				
				image:
				  repository: nginx
				  pullPolicy: IfNotPresent
				  tag: "latest"
				
				service:
				  type: NodePort
				  port: 80
				  nodePort: 30080


This is the configuration file - users modify this to control the deployment. 
These values are injected into the templates dynamically. 


### templates 

This is where actual kubernetes YAML templates are located. 


### deployments.yml

Defines the deployment resource - it manages pods. 

		apiVersion: apps/v1
		kind: Deployment
		metadata:
		  name: {{ include "nginx-nodeport.fullname" . }}
		spec:
		  replicas: {{ .Values.replicaCount }}
		  selector:
		    matchLabels:
		      app: {{ include "nginx-nodeport.name" . }}
		  template:
		    metadata:
		      labels:
		        app: {{ include "nginx-nodeport.name" . }}
		    spec:
		      containers:
		        - name: nginx
		          image: "{{ .Values.image.repository }}:{{ .Values.image.tag }}"
		          ports:
		            - containerPort: 80


