
Amazon Elastic Container registry (ECR) is a fully managed AWS Container image registry service that is secure , scalable and reliable .

It supports both private and public repositories , allowing developers to store manage and deploy docker 


Amazon ECR is a managed Docker registry Service. 

**Components of Amazon ECR:** 

* **Registry :**  Each AWS account has an access to Amazon ECR registry. In registry , we can create image repositories and we can also store its images. 

* **Authorization Token :**  Before pushing and pulling of images, your docker client must authenticate to Amazon ECR registries as an AWS user. The amazon web services command line interface(CLI) has a command called *get-login*  which provides the user with an authentication credentials to be passed to docker. 

* **Repository :**  The docker images is contained inside the ECR image repository. 

* **Image :** The user can very easily push and pull images to their docker repositories 