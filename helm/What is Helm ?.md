	
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


## How Helm works

1. **Helm Chart** : A helm chart is a folder that contains all the YAML templates and values file to provide a dynamic configurations . 

Folder structure looks like : 


		mychart/
		├── Chart.yaml        # Chart metadata
		├── values.yaml       # Default config values
		└── templates/
		    ├── deployment.yaml
		    ├── service.yaml
		    └── ingress.yaml


2. **Installing a chart**: 
	Run : 
		
			helm install my-release ./mychart

	Helm will: 
	* Read `values.yaml`
	* Render all templates under `template/` using these values


3. **Templates and Values**: 
	* Templates contain placeholders using Go templating
	* You can override values in values.yml 
		
			helm install my-release ./mychart -f custom-values.yaml

4. **Upgrading a release**:

	Modify the chart or values and run 

			helm upgrade my-release ./mychart

5. **RollBack support** : 

	Helm keeps a history of your releases and you can rollback if needed . 

				helm rollback my-release 1

6. **Repositories**: 

	You can fetch and install charts from public repositories (like Bitnami or ArtifactHub etc. )

			helm repo add bitnami https://charts.bitnami.com/bitnami
			helm install my-redis bitnami/redis



