
**Helm** is a package manager for kubernetes that simplifies the deployment and management of applications. 
It uses **charts** as its package format. 

Helm charts help you define , install and upgarde event the complex kubernetes applications 


**What is a helm chart ?** 
A helm chart is a package format used by helm, which is a package manager for kubernetes. 

A **chart** is a collection of files that describe a related set of Kubernetes resources . 

think of helm chart like : 
A template + configuration + metadata bundle that lets you deploy apps easily in kubernetes. 


##### What's inside the helm chart  ?

A helm chart typically includes : 

`Chart.yaml` : Metadata about the chart (name , version etc. )
`values.yaml`: Default configuration values (can be overridden )
`template/`: kubernetes yaml files written with GO templating (e.g deployment.yaml , service.yaml)



### Why use helm charts ?

- **Simplifies Deployment :** one command can install or update your app
- **Templating :** Reuse configs with variables 
- **Version Control** : Versioned like other package
- **Repeatable Deployments** : Great for CI/CD pipelines. 



## The Chart file Structure

A chart is organized as a collection of files inside a directory . The directory name is the name of the chart. Thus , a chart describing WordPress would be stored in a `wordpress/` directory. 

Inside of this directory , helm will expect a structure that matches this . 

```text
wordpress/
  Chart.yaml          # A YAML file containing information about the chart
  LICENSE             # OPTIONAL: A plain text file containing the license for the chart
  README.md           # OPTIONAL: A human-readable README file
  values.yaml         # The default configuration values for this chart
  values.schema.json  # OPTIONAL: A JSON Schema for imposing a structure on the values.yaml file
  charts/             # A directory containing any charts upon which this chart depends.
  crds/               # Custom Resource Definitions
  templates/          # A directory of templates that, when combined with values,
                      # will generate valid Kubernetes manifest files.
  templates/NOTES.txt # OPTIONAL: A plain text file containing short usage notes
```


