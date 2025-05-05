


### How would you optimize a slow CI pipeline ?

* **Parallelization**: Run tests and build in parallel stages. 
* **Caching :** Use dependency caching 
* **Selective Builds** : 
* **Matrix Builds** : Run jobs across environments in parallel using matrix strategy. 
* **Fail fast** : Exit early on failures. 


### How should secrets be managed in CICD pipeline ?


*  Store secrets in the CI/CD tool's secret management (eg. GitHub Secrets , Jenkins Credentials etc. )
* Never hardcode secrets in code or pipeline YML
* Use Environment variables at runtime
* For Cloud Deployments, prefer IAM roles 


### How do you resolve CI test failures that pass locally ?

* Check for environment differences 
* Review test flakiness or timing issues. 
* Ensure tests do not depend on local state or services 


