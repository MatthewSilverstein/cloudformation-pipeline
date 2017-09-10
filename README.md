
# Cloudformation Boilerplate For Continuous Deployments with CodePipeline/CodeBuild

This repo creates a fully managed AWS CodePipeline that automatically builds and deploys everytime code is committed to GitHub. Deployments can use complex commands through the command line. 

## Pipeline stages
Source (GitHub)

-----↓-----

Build (CodeBuild)

-----↓-----

Deploy Alpha (CodeBuild)

-----↓-----

Deploy Beta (CodeBuild)

## Using This Template
This template can be used either through the AWS CLI or through the Cloudformation Create Stack.

### AWS CLI
aws cloudformation deploy --template-file cloudformation.yaml --stack-name <stack-name> --capabilities CAPABILITY_NAMED_IAM

### AWS Cloudformation Create Stack
Go to https://console.aws.amazon.com/cloudformation/home?region=us-east-1#/stacks/new

Load the template from s3: 