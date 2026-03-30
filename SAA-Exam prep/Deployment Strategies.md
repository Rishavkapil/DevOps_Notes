
## In-Place Deployments

In this strategy, the previous version of the application on each compute resource is stopped, latest application is installed and the new versions is started and validated. 

This allows the application deployments to proceed without creating new infrastructure. 

With an in-place deployment, you can deploy your application without creating new infrastructure; however the availability of your application can be affected during these deployments. 

This approach also minimizes infrastructure costs and management overhead associated with creating new resources. 
You can use a load balancer so that each instance is deregistered during its deployment and then restored to service after the deployment is complete. 


## Blue Green Deployment

Blue/Green deployment, sometimes referred to as red/black deployment. It is a technique of releasing applications by shifting traffic between two identical environments running different versions of the application. Blue/Green deployment helps you minimize downtime downtime during application updates, mitigating risks surrounding downtime and rollback functionality. 

Blue/Green deployments enable you to launch a new version(green) of your application alongside the older version(blue), and monitor and test the new version before you reroute traffic to it, rolling back on issue detection. 

Like we have staging and production environments, when we have new update , we make changes to staging environment, and if that works fine , we promote the staging to be the new production, and production environment becomes staging. 


## Canary Release Deployment

The purpose of Canary Release Deployment is to reduce risk of deploying new versions that impacts the workload. The method will incrementally deploy the new versions, making it visible to new users in a slow fashion. As you gain confidence in the deployment, you will deploy it to replace the current versions in its entirety. 


## Linear Deployment

Linear Deployment means traffic is shifted in an equal number of minutes between each increment.
You can choose from predefined linear options that specify the percentage of traffic shifted in each increment and the number of minutes between each increment. 


## All-at-once Deployment

All-at-once means all traffic is shifted from the original environment to the replacement environment all at once. 