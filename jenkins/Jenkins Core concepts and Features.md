
#### 1. Jenkins Pipeline 


A Jenkins pipeline represents an end-to-end workflow build for CI/CD using multiple tools.
It defines the required steps to build , test , deliver/deploy applications automatically through various environments. 

Pipelines are defined using YAML files and in context of Jenkins, this file is named "Jenkinsfile"

![[Pasted image 20250303120802.png]]


#### 2. Builds in Jenkins

Builds in Jenkins refers to the stage in which the application source code is compiled , tested and packed into a deployable artifact. A build can be triggered manually or automatically , where the Jenkins automation server polls for changes in source code repository. 
Depending on the programming language in which the software is being developed , various plugins are available to support the build process in Jenkins. 


#### 3. Jenkins triggers 

As the name suggests , triggers are actions or events that initiate the build or deploy pipeline. Jenkins support various types of triggers. 

1. **SCM Triggers :** Jenkins polls for changes to the SCM repository. When the changes are found, Jenkins start executing the pipeline jobs and processes the latest source code. 
2. **Parameterized triggers:** Builds to be triggered based on user define inputs.
3. **Manual triggers:**  You need to explicitly trigger the pipeline by logging into the jenkins environment. 
4. **Time Based triggers :** triggered based  on specific schedule . A cron job is set to start the pipeline execution after every set interval. 
5. **Webhooks:**  when the pipeline runs depending on some event occurring in an external platform, we can use webhooks to trigger the pipeline execution in Jenkins.


#### 4. Jenkins artifacts

Artifact are the files that emerges from a build process, needed for the deployment or for reporting purposes. 
Jenkins provide artifact management , which allows users to publish or archive locally on the jenkins server or on an external platform 

Jenkins artifacts are the files that are generated during the execution of pipeline that can be stored and managed by Jenkins. 

#### 5. Jenkins agents

