

### Scripted Pipeline 

Scripted Pipeline is the original pipeline syntax for Jenkins and is based on Groovy scripting language. 

In Scripted Pipeline , the entire workflow is defined in a single file called Jenkins file. 

The Jenkins pipeline is written in groovy and is executed by Jenkins pipeline plugin . 

Scripted Pipeline provides lot of flexibility and control over the Workflow, 

Example of Scripted Pipeline : 

			node {  
			stage('Build') {  
			// Build the application  
			sh 'mvn clean install'  
			}  
			stage('Test') {  
			// Run the tests  
			sh 'mvn test'  
			}  
			stage('Deploy') {  
			// Deploy the application  
			sh 'deploy.sh'  
			}  
			}



In this example , we define a pipeline that has three stages : Build , test and Deploy. Each stage is executed in Jenkins node, and we use the `sh` step to run the shell commands.


#### Declarative Pipeline

Declarative pipeline is the more recent addition to jenkins and provides more structured and simpler syntax for defining the pipelines. 
It is also based on groovy programming language , but it uses Groovy based DSL(Domain-Specific Language) for pipeline configuration. 


The main Benefit of Declarative Pipeline is its readability and ease of use . 

Example of Declarative Pipeline : 


			pipeline {  
			agent any  
			stages {  
			stage('Build') {  
			steps {  
			// Build the application  
			sh 'mvn clean install'  
			}  
			}  
			stage('Test') {  
			steps {  
			// Run the tests  
			sh 'mvn test'  
			}  
			}  
			stage('Deploy') {  
			steps {  
			// Deploy the application  
			sh 'deploy.sh'  
			}  
			}  
			}  
			}


In this example , we define a pipeline using the `pipeline` block , and we specify the agent to run the pipeline on any available node , we then define the three stages using the `stage` block, and we use `steps` block to define the steps for each stage. 

###### Groovy DSL 

A Groovy-based Domain specific language (DSL) is a programming language designed to solve a specific problem efficiently within groovy.





| Scripted Pipeline                                                 | Declarative Pipeline                                             |
| ----------------------------------------------------------------- | ---------------------------------------------------------------- |
| Syntax Based on groovy Scripting language.                        | also based on groovy Scripting language but it is more specific. |
| Provides more flexibility and control over the pipeline workflow. | Simpler and more structured Syntax.                              |
| Allows more granular error handling and recovery mechanism.       | Simpler error handling mechanism that is easier to understand.   |
| Allows more code reuse and modularity                             | more self-contained and less reliant on external scripts.        |


Scripted pipeline gives more control 