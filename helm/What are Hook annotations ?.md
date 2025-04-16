
In Helm , Hook annotations are special metadata that you add to your kubernetes manifests to tell Helm when certain resources should be executed in helm life-cycle (like before install, after upgrade etc. )


### What is a Hook in Helm ?

A Hook is a kubernetes manifest (usually a pod or job ) that helm runs at a specific points in a release life-cycle, such as: 
before installation , after installation or after deletion etc. 

#### How to define a Hook annotation ?

You define a hook using annotation in the hook's metadata. 

			metadata:
			  annotations:
			    "helm.sh/hook": pre-install


#### Common Hook lifecycle events 

pre-install : Before the release is installed 
post-install : After the release is installed 
pre-delete: Before the release is deleted 
post-delete : After the release is deleted. 
etc. 

#### Example: A Job that Runs Before Install

				apiVersion: batch/v1
				kind: Job
				metadata:
				  name: migrate-database
				  annotations:
				    "helm.sh/hook": pre-install
				spec:
				  template:
				    spec:
				      containers:
				        - name: migrate
				          image: my-image
				          command: ["sh", "-c", "python migrate.py"]
				      restartPolicy: Never



kubectl create secret docker-registry regcred \
  --docker-server=124355654427.dkr.ecr.ap-south-1.amazonaws.com \
  --docker-username=AWS \
  --docker-password=$(aws ecr get-login-password --region ap-south-1) \
  --docker-email=any@email.com \
  --namespace=disaster-relief
