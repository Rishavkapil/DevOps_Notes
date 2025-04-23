

# Step 1 : Your mongobd statefulset should be deployed in the EKS cluster. 


# Step 2 : Mongo Express Deployment


You deployed mongo express with a simple deployment yml file : 


### Step 1 : Create a secret 


If mongodb is using authentication , create  a secret : 

			apiVersion: v1
			kind: Secret
			metadata:
			  name: mongo-secret
			type: Opaque
			data:
			  mongo-user: bW9uZ291c2Vy # base64 encoded
			  mongo-password: bW9uZ29wYXNz # base64 encoded


Use `echo -n 'mongouser' | base64` to encode values.




### Step 2 : Create a mongo-express deployment



			apiVersion: apps/v1
			kind: Deployment
			metadata:
			  name: mongo-express
			spec:
			  replicas: 1
			  selector:
			    matchLabels:
			      app: mongo-express
			  template:
			    metadata:
			      labels:
			        app: mongo-express
			    spec:
			      containers:
			      - name: mongo-express
			        image: mongo-express
			        ports:
			        - containerPort: 8081
			        env:
			        - name: ME_CONFIG_MONGODB_SERVER
			          value: mongodb-0.mongodb
			        - name: ME_CONFIG_MONGODB_ENABLE_ADMIN
			          value: "true"
			        - name: ME_CONFIG_BASICAUTH_USERNAME
			          value: admin
			        - name: ME_CONFIG_BASICAUTH_PASSWORD
			          value: admin
			


### Step 3 : Expose the mongo-express using service


			apiVersion: v1
			kind: Service
			metadata:
			  name: mongo-express
			spec:
			  selector:
			    app: mongo-express
			  ports:
			    - protocol: TCP
			      port: 8081
			      targetPort: 8081
			  type: NodePort  # or LoadBalancer, depending on your setup




Apply all the files :)


