

There are mainly two ways by which you can deploy your eks cluster : 
1. With GUI
2. With CLI or eksctl 


eksctl is a command line tool for creating and managing eks clusters. 

To deploy website using ingress controller, first we need to create a deployment file and service file 

then you need to eks cluster

you can create on with the eksctl using

## Step 1 : Creating EKS cluster

				eksctl create cluster \
				  --name my-cluster \
				  --region ap-south-1 \
				  --nodegroup-name my-nodes \
				  --nodes 1 \
				  --node-type t3.medium \
				  --with-oidc \
				  --managed



## Step 2 : Tag Public subnets 

Then we need to tag the subnets 
First, grab the subnet IDs for your cluster’s VPC:


			aws eks describe-cluster \
			  --name my-cluster \
			  --region ap-south-1 \
			  --query "cluster.resourcesVpcConfig.subnetIds" \
			  --output text


Then for each public subnet (the ones with an Internet Gateway route), tag them like this:

			aws ec2 create-tags \
			  --resources subnet-xxxxx subnet-yyyyy subnet-zzzzz \
			  --tags Key=kubernetes.io/role/elb,Value=1



If you’re not sure which are public, you can re-run:


			aws ec2 describe-route-tables \
			  --filters Name=association.subnet-id,Values=subnet-xxxxx \
			  --region ap-south-1 \
			  --query "RouteTables[*].Routes[*].GatewayId" \
			  --output text



Look for igw- in the output — that confirms it's public.



## Step 3 : Creating the IAM Policy + Service account for ALB policy 

1. Create IAM policy 
2. Create service account : 


			eksctl create iamserviceaccount \
			  --cluster=my-cluster \
			  --namespace=kube-system \
			  --name=aws-load-balancer-controller \
			  --attach-policy-arn=arn:aws:iam::124355654427:policy/AWSLoadBalancerControllerIAMPolicy \
			  --approve



## Step 4 : Install the AWS Load Balancer Controller (via helm) 

We’ll install the controller into your EKS cluster so it can automatically provision ALBs for Ingress resources.



1. **Pre-Req: Add the Helm repo**

			helm repo add eks https://aws.github.io/eks-charts
			helm repo update


2. **Install the controller using Helm** 

Run this command — make sure to replace the <cluster_name> with your actual cluster name if different:


	helm install aws-load-balancer-controller eks/aws-load-balancer-controller \
	  -n kube-system \
	  --set clusterName=my-cluster \
	  --set serviceAccount.create=false \
	  --set serviceAccount.name=aws-load-balancer-controller \
	  --set region=ap-south-1 \
	  --set vpcId=$(aws eks describe-cluster \
	    --name my-cluster \
	    --region ap-south-1 \
	    --query "cluster.resourcesVpcConfig.vpcId" \
	    --output text)


**Verify its working** 

	kubectl get pods -n kube-system | grep aws-load-balancer-controller

you should see something like : 

	aws-load-balancer-controller-xxxx   1/1     Running


## Step 5 :  Deploy your application 


	kubectl apply -f deployment.yml
	kubectl apply -f service.yml




## Step 6 : Create an Ingress Resource 

Lets expose your application using Ingress resource. 

Create a `ingress.yml` file 


		apiVersion: networking.k8s.io/v1
		kind: Ingress
		metadata:
		  name: frontend-ingress
		  annotations:
		    kubernetes.io/ingress.class: alb
		spec:
		  rules:
		    - http:
		        paths:
		          - path: /
		            pathType: Prefix
		            backend:
		              service:
		                name: frontend-service
		                port:
		                  number: 80



Then apply it : 

		kubectl apply -f ingress.yml


### Now wait for the alb to be provisioned 

It will take couple of minutes for the Application Load Balancer(ALB) to be created by the controller. To track the progress , run : 


		kubectl get ingress

