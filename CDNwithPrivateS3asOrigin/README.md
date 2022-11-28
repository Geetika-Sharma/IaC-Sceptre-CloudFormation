#  IaC - Sceptre - CloudFormation for CloudFront and S3
This mini project contains Sceptre/CloudFormation code (IaC) to create CloudFront with S3 as Origin

## Features

- Creates CloudFront distribution with S3 as origin
- IAM User that can access to read from and write to S3 bucket and create Cache Invalidation in CDN. It's access key is stored in SSM
- Create 'A' record in Route 53 with HostedZoneId: Z2FDTNDATAQYW2 - This is always the hosted zone ID when you create an alias record that routes traffic to a CloudFront distribution
- Dummy SSM parameters assuming the application reads the latest version from the SSM parameters
- Private S3 bucket that will host the application and a logging bucket that stores the logs of application bucket


## Pre-requisites
- AWS credentials configured
- config.yaml and other configuration files to be updated with the required values
- Executing all the files at once could result in circular dependency as CDN requires S3 bucket ARN and S3 policy requires CDN canonical user. Suggested to create S3 bucket first then CDN then Bucket policy

## Commands to setup python virtual environment

```
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

## Command to create infrastructure
```
cd sceptre
sceptre launch ssm
```

## Additional notes
Use the following command if you want to validate the config files first:

```
sceptre validate ssm/parameters.yaml
```
