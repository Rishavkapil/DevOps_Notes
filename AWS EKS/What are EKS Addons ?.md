
Amazon EKS addons are software components that provide additional functionalities to the kubernetes applications, such as networking , service discovery , and name resolution. 



**Some examples of EKS addons :** 

**VPC CNI :** Handles pod networking in your AWS VPC. 
**kube-proxy:** Handles networking rules on pods for service routing. 
**AWS Cloudwatch logs** : Sends logs from your cluster to cloud watch. 

etc. 


### Why are they useful ?

You don't have to manually upgrade or install them. 
Integrated with IAM. 



### How to install and manage them : 


You can either use AWS Console, AWS CLI , or eksctl 

Using AWS CLI : 

			aws eks create-addon \
			  --cluster-name my-cluster \
			  --addon-name vpc-cni \
			  --addon-version latest \
			  --region ap-south-1

To list the installed addons : 

		aws eks list-addons --cluster-name my-cluster --region ap-south-1
