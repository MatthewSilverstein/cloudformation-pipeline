# Cloudformation Boilerplate For Continuous Deployments with CodePipeline/CodeBuild

This repo creates a fully managed AWS CodePipeline that automatically builds and deploys everytime code is committed to GitHub.

## Pipeline stages
Source (GitHub)

-----↓-----

Build (CodeBuild)

-----↓-----

Deploy Alpha (CodeBuild)

-----↓-----

Integration Test Alpha (CodeBuild)

-----↓-----

Deploy Beta (CodeBuild)

## Setting up the pipeline
1) Install awscli and setup aws account
1) Create a GitHub repository
1) Get an access key for GitHub repository with privilleges: [admin:repo_hook, repo]
1) In commandline:

```
aws cloudformation deploy --template-file cloudformation-pipeline.yaml --stack-name <stack-name> --capabilities CAPABILITY_NAMED_IAM --parameter-overrides \
 GitHubUser=<username> \
 Repo=<repo> \
 Branch=<branch> \
 GitHubToken=<github access token>
```

## Configuring build, deployments, and tests
By default, there are three buildspec files used by this pipeline:
1) buildspec-build.yml: This is used by the Build phase of the pipeline
2) buildspec-deploy.yml: This is used by the Deployment phases of the pipeline
3) buildspec-integration-tests.yml: This is used by the Integration Test phase