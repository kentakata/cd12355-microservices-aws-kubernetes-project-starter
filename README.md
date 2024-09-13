# How to deploy coworking app

## Analytics Part

The analytics part is implemented in the analytics directory.
analytics/Dockerfile is used to build the docker images.

## Building Docker images

CodeBuild is used to build the docker images if the source code is updated.
The setting is written in buildspec.yml and the images will be uploaded to ECR.

## Kubectl setting files

All the setting files for kubectl are stored in the deployment directory.
Databese-related settings are written in configmap.yaml.
coworking.yaml is the main setting file and it refers configmap.yaml.
