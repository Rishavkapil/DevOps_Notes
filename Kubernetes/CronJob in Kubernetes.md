Kubernetes cronjobs are used for scheduling repetitive tasks such as taking backups, or monitoring , data syncing 

### Types 

1. **Basic Cronjobs :** Simple cronjob-based scheduling of recurring tasks. 

2. **Concurrency Policy :** Specify how to handle concurrent executions of a CronJob

3. **Job History Limits:** Control the number of successful and failed job completions retained by a CronJob. 


### Examples of each type 


###### Basic CronJobs : 


```
apiVersion: batch/v1
kind: CronJob
metadata: 
  name: basic-cronjob
spec:
  schedule: "*/1 * * * *"
  jobTemplate:
    spec:
      template:
        spec:
          containers:
          - name: basic-container
            image: busybox
            command: ["echo","Hello from basic CronJob"]
          restartPolicy: Never
```


###### Concurrency Policy 

```
apiVersion: batch/v1
kind: CronJob
metadata: 
  name: concurrency-cronjob
spec:
  schedule: "*/1 * * * *"
  concurrencyPolic: Forbid     # Do not allow concurrent executions
  # Allowed values are 
  # Allow (default)
  # Forbid
  # Replace
  jobTemplate:
    spec:
      template:
        spec:
          containers:
          - name: concurrency-container
            image: busybox
            command: ["echo","Hello from the concurrency CronJob"]
          restartPolicy: Never
```


Allowed values for concurrency Policy : 

* Allow : The cronJob allows concurrently running jobs

* Forbid : The cronjob does not allow concurrent runs; if it is time for a new job run and the previous job hasn't completed yet , the cronjob skips the new job. 

* Replace: If it is time for a new job run and the previous hasn't completed yet , then the cronjob replaces the currently running job with the new job run .