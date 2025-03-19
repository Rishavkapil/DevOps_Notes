
You can automate, customize and execute your software development workflows right in your repository with GitHub actions. 

**GitHub Actions** is a continues Integration and Continues delivery platform that allows you to automate your build, test and deployment pipeline . You can create workflows that build and test every pull request to your repository. 

For example , you can run a workflow to automatically add the appropriate labels whenever someone creates a new issue in your repository . 

#### The components of GitHub Actions

You can configure a GitHub actions workflow to be triggered when an event occurs in your repository , such as pull request being opened or an issue being raised. 

Your workflow Contain one or more jobs which can run in sequential order or in parallel. 

Each job will run inside its own virtual machine runner , or inside a container and has one or more steps that either run a script that you define or run an action

#### Workflow

A workflow is a configurable automated process that will run one or more jobs . 

Workflows are defined by a YAML file checked in to  your repository and will run when triggered by an event in your repository and will run when triggered by an event in your repository . 

Workflows are defined in the `.github/workflows` directory in a repository . 
A repository can have multiple workflows each of which can have different set of tasks . 

#### Events

An event is a special activity in a repository that triggers a workflow run . 

#### Jobs

A job is a set of steps in a workflow that is executed on the same runner. 
Each step is either a shell script that will be executed or an action that will run .
Steps are executed in order and are dependent on each other. 

since steps are executed in same runner , you can share data from one step to another 



#### Actions

An **Action** is a custom application for GitHub action platform that performs a complex but frequently repeated task. 

An action can pull your git repository from GitHub , setup the correct toolchain for the build environment , or setup the authentication for your cloud provider. 

#### Runners

A **runner** is a server that runs your workflows  when they're triggered . Each runner can run a single job at a time. 