Configmap is a kubernetes object that is used to store configuration data in the form of key-value pairs. It is used to **separate configuration from application code.** 



#### Why use configmap ?


Imagine you have an app that connects to a database, and it needs , 

* A database URL 
* A port number


Instead of hardcoding that into your app, you can : 

- store it in a configmap
- Mount it to your pod 
- Easily change configs without rebuilding your app. 


For example ,

			apiVersion: v1
			kind: ConfigMap
			metadata:
			  name: my-config
			data:
			  DB_URL: "postgres://mydb:5432"
			  FEATURE_FLAG: "true"
			  APP_MODE: "production"



