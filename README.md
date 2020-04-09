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

## Import Ceritificate Using AWS CLI
The following example shows how to import a certificate using the AWS Command Line Interface (AWS CLI). The example assumes the following: 

1. The PEM-encoded certificate is stored in a file named Certificate.pem. Use the following command to export your .crt or.cert file into .pem file
```bash
openssl x509 -in <youCrtFile>.crt -out <youCertName>.pem
```

2. The PEM-encoded certificate chain is stored in a file named CertificateChain.pem. Use the following command to export your .ca-bundle file into .pem file
```bash
openssl x509 -in <yourCaBundleFile>.ca-bundle -out <yourCertChainName>.pem
```

3. The PEM-encoded, unencrypted private key is stored in a file named PrivateKey.pem.

4. THe following command imports the certificate to Amazon Certificate Manager.
```bash
$ aws acm import-certificate --certificate file://<youCertName>.pem --certificate-chain file://<yourCertChainName>.pem --private-key file:/<yourPrivateKey>.pem
  	
```