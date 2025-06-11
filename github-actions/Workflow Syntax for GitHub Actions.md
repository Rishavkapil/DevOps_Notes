
A workflow is a configurable automated process made up of one or more jobs. You must create a YAML file to define your workflow configuration. 



###### About YAML syntax for workflow
Workflows file define YAML syntax and you must have either a .yml or .yaml file extension .

You must store workflow files in the `.github/workflows` directory of your repository. 


**`name` :** 

The name of the workflow . Github displays the name of your workflows under your repository's "Action" tab. If you omit name , GitHub displays the workflow file path relative to the root of the repository.


**`run-name`  :** 

The name for workflow runs generated from the workflow. GitHub displays the workflow run name in the list of workflow run on your repository's action. 

If the `run-name` is omitted or is only whitespace, then run name is set to event specific information for the workflow run. 

For Example, for  a workflow triggered by a `push` or `pull_request` event , it is set as the commit message or the title of the `pull_request`


**Example of run-name :** 

```yaml
run-name: Deploy to ${{inputs.deploy_target }} by @${{ github.author }}
```


**`on ` :**

To automatically trigger a workflow, use `on` to define which events can cause the workflow to run. 

You define single or multiple events that can trigger a workflow, or set a time schedule. 

You can also restrict the execution of a workflow to only occur for specific files, tags or branch changes. 

**using an single event :** 

For example , a workflow with the following `on` value will run when a push is made to any branch in the repository or when someone forks the repository: 

	on: push 

**Using Multiple events :** 

You can specify a single or multiple events. For example , a workflow with the following `on` value will run when a push is made to any branch in the repository or when someone forks the repository. 

	on: [push , fork]

If you specify multiple events, only one of those needs to occur when your workflow should run. 

Use `on.<event_name>.types`  to define the type of event activity that will trigger a workflow run. 

For example, the `issue_comment` event has created, edited and deleted activity types. 
If your workflow triggers on `label` event , it will run whenever a label is created, edited or deleted. 

If you specify the "created" activity type for the label event, your workflow will run when the label is edited or deleted. 

```yaml
on:
  label:
    types:
      - created
```


**`on.<event_name>.types` :**


Use `on.<event_name>.types` to define the type of activity that will trigger a workflow run. Most GitHub events are triggered by more than one type of activity  . 

For example , the `label` is triggered when a label is `created` , `edited` or `deleted` . 

The types keyword enables you to narrow down activity that causes the workflow to run. 

When only one activity type triggers a webhook event, the `types` keyword is unnecessary . 

```yaml
on:
  label:
    types: [created, edited]
```


 **`on.<pull_request|pull_request_target>.<branches|branches-ignore`**: 


 