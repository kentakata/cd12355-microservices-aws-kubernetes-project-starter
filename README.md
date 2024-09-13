# About Coworking Space Service

The Coworking Space Service is a set of APIs that enables users to request one-time tokens and administrators to authorize access to a coworking space.

This project uses the following cloud services:

* GitHub - source code repository
* AWS CodeBuild - build Docker images remotely
* AWS ECR - host Docker images
* AWS EKS - run applications in k8s
* AWS CloudWatch - monitor activity and logs in EKS


## Analytics app

The analytics app is implemented in the analytics directory.
analytics/Dockerfile is used to build the docker images.

### APIs

The app has the following API endpoints:
* /health_check - for health check
* /readiness_check - for readiness check
* /api/reports/daily_usage - reports the daily usage
* /api/reports/user_visits - reports the user visits

### Configurations

The app can be configured by the following environment variables:
* DB_USERNAME
* DB_PASSWORD
* DB_HOST
* DB_PORT
* DB_NAME

They are used when connecting the database.


## Building Docker images

AWS CodeBuild is used to build the docker images if the source code is updated.
The setting is written in buildspec.yml and the images will be uploaded to AWS ECR.


## Kubectl setting files

All the setting files for kubectl are stored in the deployment directory.
Database-related configurations are written in configmap.yaml.
coworking.yaml is the main setting file and it refers configmap.yaml.

The following files are used to deploy the database service:
* postgresql-deployment.yaml
* postgresql-service.yaml
* pv.yaml
* pvc.yaml


## Monitoring

The status of the Coworking Space Service can be monitored via AWS CloudWatch.
