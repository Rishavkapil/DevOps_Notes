
In kubernetes, a **Job** is a resource used to execute one-off tasks that must be reliable run to completion. 

A Job creates one or more Pods and will continue to retry execution of the Pods until a specified number of them successfully terminated. As pods successfully completes, the job tracks the successful completions . 

Deleting a job will clean up the pod it created. 

Suspending a job will deletes its active pods until the job is resumed again . 



**Jobs** are a way to **run one-time or batch tasks** . Unlike regular pods that are designed to keep running (like web servers ) , a job ensures that a specified number of pods run to completion successfully. 


### Use Cases of Kubernetes jobs 

* Data processing tasks. 
* Running Database migrations. 
* Sending Bulk emails 

##### Example 


		apiVersion: batch/v1
		kind: Job
		metadata:
		  name: example-job
		spec:
		  template:
		    spec:
		      containers:
		      - name: pi
		        image: perl
		        command: ["perl",  "-Mbignum=bpi", "-wle", "print bpi(2000)"]
		      restartPolicy: Never
		  backoffLimit: 4




