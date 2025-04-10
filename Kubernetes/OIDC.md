
# What is OIDC ?


**OIDC(OpenID Connect)** is an authentication protocol that works on top of ==OAuth 2.0==. It lets users login using Identity providers like google , GitHub etc. 

* OAuth 2.0 = Authorization (can access my data?)
* OIDC = Adds authentication (who are you ?)


**OAuth 2.0 :** is an authentication framework that lets app access user data (like email , photos, calendar etc. ) from another service without getting the user's password. 
It is commonly used to allow secure delegated access. For example , 

* You login to a website using "Login with Google"
* The website doesn't see your Google password
* Google gives the site a token to access certain info. (like your email). 


## Why use OIDC in kubernetes ?

Kubernetes doesn't manage user accounts or passwords . Instead it allows external identity providers to handle authentication . 

This is useful for : 
* Container authentication 
* Better security and access control 



## How OIDC works in Kubernetes ?


### Step 1 : Login (user side)

You (the user ) authenticate using an OIDC compatible tool (like kube-login or oidc-login plugin for kubectl ) or via web portal . 

* the client redirects you to the identity Provider(e.g Google)
* You login there (google checks your password )
* After successful login , the IDp issues 
	* an Id token(JWT - json web token)
	* possible an access token or fresh token


### Step 2 : kubectl sends token to Kubernetes API server 

you run command like 

			kubectl get pods

Your kubeconfig is configured to use OIDC . It attaches the token ID in the authorization : bearer < token > 


### Step 3 :  Api server validates the token 

When all the checks pass , the kubernetes will know who you are 



### Step 4 : Kubernetes identifies the user 


From the token id , the kubernetes extracts the details of the users . 


### Step 5 : Kubernetes authorizes you (RBAC)


Once authenticated, kubernetes runs its RBAC( Role based access Control ) checks : 


			apiVersion: rbac.authorization.k8s.io/v1
			kind: RoleBinding
			metadata:
			  name: pod-reader
			  namespace: default
			subjects:
			- kind: User
			  name: "you@example.com"   # Must match your token's claim
			roleRef:
			  kind: Role
			  name: read-pods
			  apiGroup: rbac.authorization.k8s.io


If your identity has the permission , kubernetes allows the action . 