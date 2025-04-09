
# What is OIDC ?


**OIDC(OpenID Connect)** is an authentication protocol that works on top of ==OAuth 2.0==. It lets users login using Identity providers like google , GitHub etc. 

**OAuth 2.0 :** is an authentication framework that lets app access user data (like email , photos, calendar etc. ) from another service without getting the user's password. 
It is commonly used to allow secure delegated access. For example , 

* You login to a website using "Login with Google"
* The website doesn't see your Google password
* Google gives the site a token to access certain info. (like your email). 


## Why use OIDC in kubernetes ?

Kubernetes doesn't manage user accounts or passwords . Instead it allows external identity providers to handle authentication . 