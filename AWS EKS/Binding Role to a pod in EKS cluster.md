
## Step 1 : Create a cluster Role 

		apiVersion: rbac.authorization.k8s.io/v1
		kind: ClusterRole
		metadata:
		  name: read-pods-namespaces
		rules:
		- apiGroups: [""]
		  resources: ["pods", "namespaces"]
		  verbs: ["get", "list"]


**kind** : ClusterRole -- defines a cluster role 
**rules**: 
* **apiGroups**  : [""] This means core api group (pods and namespaces belong here)
* **resources** : specifies which resources are accessible (eg. pods and namespaces here)
* **verbs** : Grants only get and list permissions , so no create/update/delete actions 


## Step 2 : Create a Service account

					apiVersion: v1
					kind: ServiceAccount
					metadata:
					  name: limited-kubectl-sa
					  namespace: default

## Step 3 : Bind cluster Role to a service account

		apiVersion: rbac.authorization.k8s.io/v1
		kind: ClusterRoleBinding
		metadata:
		  name: bind-read-pods-namespaces
		subjects:
		- kind: ServiceAccount
		  name: limited-kubectl-sa
		  namespace: default
		roleRef:
		  kind: ClusterRole
		  name: read-pods-namespaces
		  apiGroup: rbac.authorization.k8s.io


**kind : clusterRoleBinding**  - Binds a cluster Role to a subject
**subjects :** This is who gets the permissions
	 A service account named `limited-kubectl-sa` in the `default namespace`

**roleRef :** This tells the binding which role to link : 
	It links the `read-pods-namespaces` Cluster Role 

This binding gives the service account access to read pods and namespaces. 


## Step 4 : Creating a Pod


				apiVersion: v1
				kind: Pod
				metadata:
				  name: kubectl-limited
				spec:
				  serviceAccountName: limited-kubectl-sa
				  containers:
				  - name: kubectl
				    image: bitnami/kubectl:latest
				    command: ["sleep", "3600"]



**kind : pod** - defines a single pod

**serviceAccountName :** Associates this pod with the **limited-kubectl-sa** service account


**Containers :** 
**image :** uses bitnami/kubectl image which has kubectl installed 
**command :** keeps the pod running by sleeping for 3600 seconds . 


when you exec into this pod , the kubectl command will run using the limited permissions of the serviceAccount. 
