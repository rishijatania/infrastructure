# AWS Infrastructure Stack - Cloud Formation


**Here what you need to do for networking infrastructure setup:**

## Post Installation Step
1. Install and setup AWS command line interface. (Refer:- https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2.html).

2. Configure your aws profile using the following command:
```zsh
$ aws configure --profile produser
AWS Access Key ID [None]: <AccessID>
AWS Secret Access Key [None]: <AccessKey>
Default region name [None]: <region>
Default output format [None]: 
```

## Steps to create AWS Infra Stack
1. Create CloudFormation template networking.json or networking.yaml that can be used to setup required networking resources.

2. Create Cloud formation Stack using the following command:
```sh
$ aws cloudformation create-stack \
  --stack-name csye6225demo \
  --parameters ParameterKey=InstanceTypeParameter,ParameterValue=value \
  --template-body file://networking.json
```
2. To Delete Cloud formation Stack use the following command.
```sh
$ aws cloudformation delete-stack --stack-name csye6225demo 
```
 ## Variables provided in CLI
 ```
 Template Name,  
 AWS Region,  
 VPC Name,  
 VPC CIDR,  
 Subnet1 CIDER,  
 subnet2 CIDER,  
 subnet3 CIDER,  
 name of the JSON file
 ```
 ## Networking setup
 1. Create a VPC(vpc)
 2. Three subnets created in the VPC
 3. Internet gateway, along with Internet gatewayVPC attachment
 4. Public Route table along with all the subnets attached to this table 
 5. Public Route in the public Router table with destination CIDR block 0.0.0.0/0 and internet gateway created as target.