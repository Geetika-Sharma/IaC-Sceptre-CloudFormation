#  IaC - Sceptre - CloudFormation for EC2 with CodeDeploy Agent
This mini project contains Sceptre/CloudFormation code (IaC) to create EC2 instance with CodeDeploy Agent and CloudWatch Agent

## Features

- Creates EC2 instance with the following features:
    - Security Group that allows specified local network
    - IAM Instance Profile with Code Deploy Role attached
    - Wait Handle and Condition for installation of CloudWatch and CodeDeploy Agent
    - 100GB additional EBS attached and logical volumes created for the same
    - CloudWatch Agent installed and configured
    - CodeDeploy Agent installed via UserData
- Creates IAM Role with the following policies:
    - Allow CloudFormation 
    - Allow sample S3 bucket with read and write access
    - Allow sample S3 bucket 2 with read access
    - Receive and Delete messages from SQS
    - Publish to SNS Topic
    - Get SSM Parameters
    - Read and Write to CloudWatch Logs
    - Read Volumes

## Pre-requisites
- AWS credentials configured
- config.yaml file updated with the required values

## Commands to setup python virtual environment

```
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

## Command to create infrastructure
```
cd sceptre
sceptre launch compute
```

## Additional notes
Use the following command if you want to validate the config files first:

```
sceptre validate compute/iam.yaml
```
