# musketeers-lambda-go-sam

[![pipeline status](https://gitlab.com/serverlesscloudlabs/musketeers-lambda-go-sam/badges/master/pipeline.svg)](https://gitlab.com/serverlesscloudlabs/musketeers-lambda-go-sam/pipelines)

musketeers-lambda-go-sam is a sample project demonstrating using [3 Musketeers](https://github.com/flemay/three-musketeers) and [GitLab CI/CD](https://about.gitlab.com/features/gitlab-ci-cd/) pipeline as code.

Go project is an [AWS Lambda in Go](https://github.com/aws/aws-lambda-go) binded to an API Gateway which returns the value of the environment variable `ECHO_MESSAGE` on a `GET /echo` request.

The [3 Musketeers](https://github.com/flemay/three-musketeers) pattern is being used to test, build, and deploy the Lambda function. [AWS SAM](https://github.com/awslabs/serverless-application-model) is the chosen framework to handle AWS deployment. GitLab CI/CD then calls the exact same test, build and deploy commands.

## Prerequisites

- [Docker](https://docs.docker.com/engine/installation/)
- [Compose](https://docs.docker.com/compose/install/)
- Make
- AWS credentials in ~/.aws or environment variables (only for deploying to AWS)

> For Windows users, PowerShell is recommended and make can be installed with [scoop](https://github.com/lukesampson/scoop).

## Usage

```bash
# create .env file based on .env.example with sample values
$ make envfile
# install dependencies
$ make deps
# test
$ make test
# compile the go function and create package for SAM
$ make build pack
# deploy to aws
$ make deploy
# remove the aws stack (api gateway, lambda)
$ make remove
# clean your folder and docker
$ make clean
```