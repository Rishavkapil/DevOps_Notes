

StatefulSets are used for applications that require persistent identity and stable storage, which is crucial for mongodb.


## Prerequisites 

*  EKS cluster setup with kubectl and helm. 
* eksctl and aws clii configured. 
* kubectl access to eks cluster. 



## Step 1 : Install the EBS CSI driver



		eksctl create iamserviceaccount \
		  --name ebs-csi-controller-sa \
		  --namespace kube-system \
		  --cluster <your-cluster-name> \
		  --attach-policy-arn arn:aws:iam::aws:policy/service-role/AmazonEBSCSIDriverPolicy \
		  --approve \
		  --role-name AmazonEKS_EBS_CSI_DriverRole
		
		eksctl utils associate-iam-oidc-provider \
		  --region <region> \
		  --cluster <your-cluster-name> \
		  --approve
		
		eksctl create addon --name aws-ebs-csi-driver \
		  --cluster <your-cluster-name> \
		  --service-account-role-arn arn:aws:iam::<account-id>:role/AmazonEKS_EBS_CSI_DriverRole \
		  --force



## Step 2 : Create a storage class



			# storage-class.yaml
			apiVersion: storage.k8s.io/v1
			kind: StorageClass
			metadata:
			  name: ebs-sc
			provisioner: ebs.csi.aws.com
			volumeBindingMode: WaitForFirstConsumer
			reclaimPolicy: Retain




## Step 3 : Create a headless service for mongodb


### What is headless service ??

A headless service is a special type of service without a clusterIP address - meaning it doesn't do load balancing and instead lets you directly reach the individual pods. 

A **normal service** hides the pod behind the single virtual IP and load balancers requests between them. But a headless service doesnot do this - it exposes each pod's DNS name individually . 

#### Real World Analogy : Pizza delivery 

Imagine you run a pizza app

you have : 
	3 pizza chefs(pods)
	A receptionist (service) who takes orders and assigns a chef. 


##### Normal Kubernetes Service

In this setup , the receptionist has one phone number (Ip address)

Everytime someone calls the receptionist picks up a random chef(load balancing)

The customer never know which chef made the pizza

**How it works**

- Kubernetes gives a service a clusterIP 
- Clients connect to this service , kubernetes randomly routes traffic to one of the pods. 
- This is good for frontend apps, api etc. 



##### Headless service

Now imagine this : 

- the customers wants to directly talk to chef-1 , chef-2 , chef-3 
- There is no receptionist(no clusterIP)
- Customers use a directory(DNS) to find each chef directory. 

**How it works**

- You set clusterIP : none -> no virtual IP assigned
- Instead of one IP , the service returns the IP address of all pods. 
- Each pod can be contacted individually by name  
			
			pod-0.mongodb.default.svc.cluster.local
			pod-1.mongodb.default.svc.cluster.local
			pod-2.mongodb.default.svc.cluster.local


### Why this is needed in mongodb 

When you run mongodb in production , you usually run it in something called replica set . 


