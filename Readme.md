# Instructions

## Pre-requisities:

0. Create AWS IAM User with API keys
1. Download and install following utilities:

   - aws-cli
   - eksctl
   - kubectl
   - helm

## Setup Kubernetes Cluster and Deploy Application:

0. Create AWS EKS Cluster:  
eg:

```
eksctl create cluster --name sjain-eks \
  --version 1.22 \
  --region us-west-1 \
  --vpc-cidr 192.168.0.0/16 \
  --nodegroup-name sjain-nodes \
  --node-type m5.large \
  --nodes 2
```

1. Setup [AWS Load Balancer Controller](https://docs.aws.amazon.com/eks/latest/userguide/aws-load-balancer-controller.html) for managing and configuring AWS ELB for a Kubernetes cluster.

2. Create ECR Repositories:  
eg: 

```
aws ecr create-repository --repository-name sample-repo \
  --region us-west-1 \
  --tags '[{"Key":"env","Value":"test"}]' \
  --image-tag-mutability MUTABLE \
  --image-scanning-configuration scanOnPush=true
```

3. Dockerize the "api" and "web" application:

    - Code:
      - API: https://github.com/sj13081985/demo-api
      - WEB: https://github.com/sj13081985/demo-web
    - Dockerfile:
      - API: https://github.com/sj13081985/demo-api/blob/master/Dockerfile
      - WEB: https://github.com/sj13081985/demo-web/blob/master/Dockerfile

4. Deploy application over AWS EKS cluster using Kubernetes configurations:

    - Kubernetes Config Files: https://git.toptal.com/screening/Saurabh-Jain1/-/tree/main/kubernetes
 
5. Setup Github actions for Continuous Deployment:

    - API: https://git.toptal.com/screening/Saurabh-Jain1/-/blob/main/continuous-deployment-workflows/api-deploy-workflow.yml
    - WEB: https://git.toptal.com/screening/Saurabh-Jain1/-/blob/main/continuous-deployment-workflows/web-deploy-workflow.yml

6. Create AWS Cloudfront Distribution for CDN  
eg:

```
aws cloudfront create-distribution --origin-domain-name <ALB_DOMAIN_NAME>
```

7. Create S3 bucket for Postgres Database backup running over EKS Cluster

8. Setup Prometheus and Grafana for metric data collection and metric visualizations.

## Application artifacts:

0. Application URL:
    - API: https://d1gsdt4qy0r4jr.cloudfront.net/api/status
    - WEB: https://d1gsdt4qy0r4jr.cloudfront.net/

1. Grafana Dashboard:
    - http://a8fa907cb658842cbb770c45fbf706b3-1186429757.us-west-1.elb.amazonaws.com/dashboards


