#  IaC - Sceptre - CloudFormation for Lambda@Edge
This mini project contains Sceptre/CloudFormation code (IaC) to create Lambda@Edge.

## Features

- Create S3 Bucket to store Lambda Function
- IAM User that has access to read and write to Lambda and update Cloud Front Distribution
- Create Lambda@edge with source code stored in previously created S3 bucket

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
sceptre launch lambda
```

## Additional notes
Use the following command if you want to validate the config files first:

```
sceptre validate lambda/lambdaatedge.yaml
```
