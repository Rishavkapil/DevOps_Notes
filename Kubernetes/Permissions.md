
In kubenetes , permissions referes to the ability of a user, group or service account to perform specific actions (like read , write , delete , list etc. ) on resources (like pods, deployments , services etc. ) within the cluster. 

These permissions are managed using role based access control(RBAC)


## Core Concepts of Kubernetes permissions 

1. Subjects - who ?
	* users (authenticated users )
	* Groups 
	* service accounts
2. Resources - what ?
	* kubernetes objects like pods, deployment , secrets etc. 

3. verbs - what can be done ?
	* Actions like get , list , create , update ,delete etc. 

4. Cluster and roles - what permissions are defined ?
	* Roles defines permissions within a namespace

5. Role binding and clusterole binding - How permissions are assigned ?
	* Role Binding : Binds a role to a user , group in a specific namespace
	* ClusterRole Binding : Binds a cluster role to a user /group across the cluster. 