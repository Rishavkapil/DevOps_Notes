

Cronjob start one-time jobs on repeating schedules. 

A CronJob is meant for performing regular scheduled actions such as backups, report generation and so on. One cronjob object is like one line of a crontab. 

It runs a job periodically on given schedule. 

A Single cronjob can create multiple concurrent jobs. 

Example : 

```
apiVersion: batch/v1
kind: CronJob
metadata:
  name: hello
spec:
  schedule: "* * * * *"
  jobTemplate:
    spec:
      template:
        spec:
          containers:
          - name: hello
            image: busybox:1.28
            imagePullPolicy: IfNotPresent
            command:
            - /bin/sh
            - -c 
            - date; echo Hello from kubernetes cluster
          restartPolicy: OnFailure
```



Now lets see what the everything do in this yaml file



**Job Template :**

The spec.jobTemplate defines a template for the jobs that the cronjob creates, and it is required. It has exactly the same schema as a job, except that it is nested and does not have an apiVersion or kind . 

**Deadline for a delayed job start :** 

The .spec.DeadlineSeconds field is optioinal . This field defines a deadline  for staring the jobs. If that job misses its scheduled time for any reasons. 
After missing a  deadline , the cronjob skips that instance of the job. For example, if you have a backup job that runs twice a day, you might allow it to start up to 8 hours late, because a backup taken any later wouldn't be useful: you would instead prefer to wait for next scheduled run. 

**Concurrency Policy :** 

The .spec.concurrencyPolicy field is optional . It specifies how to treat concurrent exceptions of a job that is created by this cronjob. This spec me specify only one of the following concurrency policies : 

* `allow` : The cronjobs allow concurrently running jobs. 
* `Forbid` : The cronjob does not allow concurrent runs; if it is time for new job run and the previous job run hasn't finished yet, the cronjob skips the new job run 


**Scheduled Suspension** 

You can suspend execution of jobs for a cronjob, by setting the optional `.spec.suspend` field to true. The field default to false. 

This setting does not affect jobs that the cronjob has already started. 