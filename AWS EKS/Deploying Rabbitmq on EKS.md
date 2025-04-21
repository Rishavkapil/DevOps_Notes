

## 1. Create a Persistent volume(PV)

			apiVersion: v1
			kind: PersistentVolume
			metadata:
			  name: rabbitmq-pv
			spec:
			  capacity:
			    storage: 2Gi
			  accessModes:
			    - ReadWriteOnce
			  storageClassName: manual
			  hostPath:
			    path: /mnt/data/rabbitmq


**What it does ?**
This file creates a persistent volume - which is a piece of storage in the kubernetes cluster. It acts like a disk that can be mounted on a container. 

`capacity-storage`: Total size of the volume 
`accessMode: `: How the volume can be accessed : `ReadWriteOnce` means only one pod can write at a time 

`storageClassName` : Label to match with PVC 

`hostPath` : Mounts a local path from the node (/mnt/data/rabbitmq) to the pod - used for /dev/testing




## 2. Creating Persistent Volume Claim (PVC)

			apiVersion: v1
			kind: PersistentVolumeClaim
			metadata:
			  name: rabbitmq-pvc
			spec:
			  accessModes:
			    - ReadWriteOnce
			  resources:
			    requests:
			      storage: 2Gi
			  storageClassName: manual



**What it does**

This file requests storage from the cluster . Think of it like saying "Hey Kubernetes , give me 2GI of storage that matches this class. "

`accessMode` :  must match the PV(ReadWriteOnce)
`resource.request.storage` : The amount of storage requested
`storageClassName` : Matches PV with same storage class. 




## 3. Creating Deployment file

		
		apiVersion: apps/v1
		kind: Deployment
		metadata:
		  name: rabbitmq
		spec:
		  replicas: 1
		  selector:
		    matchLabels:
		      app: rabbitmq
		  template:
		    metadata:
		      labels:
		        app: rabbitmq
		    spec:
		      containers:
		        - name: rabbitmq
		          image: rabbitmq:3-management
		          ports:
		            - containerPort: 5672    # AMQP (message protocol)
		            - containerPort: 15672   # Web UI
		          volumeMounts:
		            - name: rabbitmq-storage
		              mountPath: /var/lib/rabbitmq
		      volumes:
		        - name: rabbitmq-storage
		          persistentVolumeClaim:
		            claimName: rabbitmq-pvc

**What it does**

This file deploys RabbitMQ using the management version . It also attaches the PVC to store message queues and broker data persistently . 



`replicas : 1 ` One 1 rabbitMQ instance 

`image` :  Uses official rabbitmq:3-management image

`containerPort 5672 ` : Default AMQP Port -- used by apps to send/receives messages

`containerPort 15672`: RabbitMQ management UI

`volumeMounts.mountPath` : where inside the container volume is mounted 

`volumes.persistentVolumeClaim.claimName` : Binds the volume to the rabbitmq-pvc




## 4. Creating Service file 

				`apiVersion: v1
				kind: Service
				metadata:
				  name: rabbitmq
				spec:
				  selector:
				    app: rabbitmq
				  ports:
				    - name: amqp
				      port: 5672
				      targetPort: 5672
				    - name: management
				      port: 15672
				      targetPort: 15672
				  type: ClusterIP


`


**What it does**

This field creates a Service to expose RabbitMQ inside the cluster. 


`selector` : Matches the pod label app: rabbitmq to route traffic 

`port ` : Port other pods use to connect 

`targetPort` : Port inside the container 

`type: ClusterIP ` : Only accessible within the cluster 




