
## Workflow 

A Workflow is a programmed process that runs one or more jobs. This configurable process is defined by a Yaml in the .github/workflows directory in a repository . This repo can have several workflows. And each workflow can perform a different set of jobs. 

For example , you can use one workflow to create and test pull request while another to deploy your application. 



## Events 

An Event is a particular activity in the repository. It is like a trigger for workflows . When the event occurs within a repository, GitHub Actions respond to them. These events can push requests, pull requests, or other Actions. 



## Jobs 

Jobs are set of steps in a workflow. They are executed under the same runner. Each step is either a shell script or an action. Scrips execute while actions run. 



## Action

An Action is the application for github actions . It performs frequently repeated tasks.


## Runner

A Runner is a server that runs workflows when they are triggered. One runner can perform single task a time. 


## Variables in Workflows

The default github actions environment variables, incorporated in every workflow, run automatically. 
However, users can customize the environment variables by setting them in their YAML files.

In the following example, you can see how one can create custom variables for POSTGRES_HOST AND POSTGRES_PORT. These variables are available in the node client.js script. 


```yaml
jobs: 
	demo-job:
		steps: 
		  - name: Connect to your postgres SQL
		    run: node client.js
		    env:
			  POSTGRES_HOST: postgres
			  POSTGRES_PORT: 5432
```


