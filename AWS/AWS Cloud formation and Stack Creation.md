
Cloud Formation uses a template based approach, where we define the infrastructure as a Code(IAAC) using JSON or YAML template. In this template file, we define the infrastructure, i.e resources and configuration. 

Cloud formation takes care of creating, updating, and deleting resources. 

In AWS CloudFormation, a stack can be defined by a CloudFormatin Template, which is a JSON or YAML file that describes the desired state of infrastructure that we want to create. It basically consist the resouces, the configuration and dependencies for the resources. 

A CloudFormation Sample Template : 

```
AWSTemplateFormatVersion: '2010-09-09'  
Description: 'Sample CloudFormation Template'  
  
Resources:  
EC2Instance:  
Type: 'AWS::EC2::Instance'  
Properties:  
ImageId: ami-********  
InstanceType: t2.micro  
KeyName: keypair-name  
SecurityGroupIds:  
- sg-*****  
SubnetId: subnet-*****  
VPC:  
Type: 'AWS::EC2::VPC'  
----  
InternetGateway:  
Type: 'AWS::EC2::InternetGateway'  
----  
Subnet:  
Type: 'AWS::EC2::Subnet'  
----  
Route:  
Type: 'AWS::EC2::Route'  
----  
S3Bucket:  
Type: 'AWS::S3::Bucket'  
----
```


* AWSTemplateFormatVersion: This specifies the version of the CloudFormation Template. 

* Description: Provides the Purpose of the template. 

* Resources : We will define the resources that we want to create.

* Type: This specifies the resource type being created. 

* Properties: We specify the properties and configuration of the resource. Like for example, for an EC2 instance, we add ImageID, Instance Type,Keyname, security groups , port numbers etc. 
