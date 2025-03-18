Jenkins is an open source **continues Integration/Continues delivery** and deployment automation software . 

With Jenkins, developers can setup pipeline defining the steps required to build , test and deploy their applications. 

It is used to implement CICD workflows called pipelines. 

CICD pipelines automate testing and reporting on isolated changes in a larger codebase in real time.

It is used to automate all sorts of tasks related to building , testing and delivering or deploying software. 

It automates build, test , and deployment tasks by executing jobs triggered by events such as new commits  , branches and pull requests across different types of environment.

### What is Jenkins used for ?

**Jenkins**  is used for several reasons in software development process. Some of them are : 

1. **Continues Intigeration :** Jenkins facilitates CI by automatically building and testing software whenever changes are made in the code base. 
2. **Automated Testing :** 
3. **Continues Delivery and Deployment(CD)**
4. **Open-Source and Cost effective** 

#### Disadvantages of Jenkins

1. **Complexity** 
2. **Maintenance Overhead** 
3. **Scalability Challenges**
4. **Dependency on Plugins**
5. **Resource Consumption**

## How does Jenkins Work ?



![[Pasted image 20250303114927.png]]




Jenkins integrates with git repositories where developers collaborate and commit code changes. Jenkins picks up these changes to automatically start the build process, which involves compilation , testing and error reporting as a feedback loop to developers. 


Numerous plugins are available for specific tasks related to version control , source code management , build , testing frameworks etc. 


### What is Pipeline ?

In software Development and CICD practices, a pipeline refers to sequence of automated steps or stages that code changes go through , from source code to deployment or release. 

A pipeline typically consists of multiple stages, each representing a distinct phase in software delivery process.These stages can include : 

1. **Checkout :**  This phase consist of retrieving the latest version of the source code from the version control system (such as Git ) to begin the pipeline process. 

2. **Build :**  In this stage, source code is compiled and built into executable artifacts or packages. 
	*  artifacts are the files generated during the build process, such as compiled binaries , test reports , configuration files etc. 

3. **Test :** Test Stage includes various types of tests including unit tests, integration tests etc. 

4. **Static Code Analysis :** This stage involves analyzing the codebase for potential issues , security vulnerabilities etc. 

5. **Deployment :** The deployment stage involves deploying the build artifacts to the desired environment, such as staging  or production. 

6. **Release :**  This stage handles the required steps to release the software. 




#### **What are Jenkins plugins ?**

Plugins in Jenkins are small independent programs that enhance and extend the functionality of Jenkins CI/CD pipeline. 


Plugins are software components that extends the functionality of Jenkins automation server. They are used to enhance and customize Jenkins to support various builds , test and deployment scenarios. 




#### Nodes in Jenkins


A **node** in Jenkins is a machine that is part of the jenkins environment and is capable of executing Pipelines or projects. 
Nodes are also know as agents, are worker machines that executes tasks assigned by the Jenkins master. 



**Jenkins Master**  is the primary Jenkins server responsible for scheduling jobs , assigning tasks to slaves and sending builds to server for execution. 


Jenkins' master/slave architecture allows you to distribute the workload of executing jenkins jobs across multiple nodes. 

The master node is responsible for managing Jenkins system, storing configurations and handling user interactions through web interfaces . 


The **Slave Nodes**  also known as agent nodes, are responsible for executing the jobs assigned to them by master . 




#### Jenkins Master


Your main jenkins server is the master . The Master's Job is to handle : 

* Scheduling build jobs 
* Dispatching builds to the slave for actual execution
* Monitoring the Slaves



#### Jenkins Slave


A Slave is a java executable that runs on a remote machine. 

Java executable is used to run jenkins servers and execute the jobs. 

* I hears requests from Jenkins master instance.
* Slaves can run on a variety of operating Systems.
* The job of the slave is to do as they are told to , which involves executing build jobs dispatched by the master.

![[Pasted image 20250312182230.png]]



