# Task details

## Summary:
You want to design a continuous delivery architecture for a scalable and secure 3-tier Node application.  
Application to use can be found on https://git.toptal.com/henrique/node-3tier-app2

## Requirements:

 - Both web and API tiers should be exposed to the internet and the DB tier should not be accessible from the internet.  
`Response` - **Done**. Web and API components are accessible over internet whereas DB tier is not accessible from the internet.

 - You should clone the repository and use it as the base for your system.  
`Response` - **Done**. Created 2 separate repositories for "Web" and "API" tier.
 - You need to create resources for all the tiers.  
`Response` - **Done**. Resources are created for Web, API and Database tier.
 - The architecture should be completely provisioned via some infrastructure as a code tool.  
`Response` - **Done**. Architecture is provisioned using AWS CloudFormation.
 - The presented solution must handle server (instance) failures.  
`Response` - **Done**. AWS EKS cluster is offering server/instance failures.
 - Components must be updated without downtime in service.  
`Response` - **Done**. All components are being updated with rolling updates and without downtime.
 - The deployment of new code should be completely automated (bonus points if you create tests and include them in the pipeline).  
`Response` - **Done**. Deployment process has been automated using Github actions.
 - The database and any mutable storage need to be backed up at least daily.  
`Response` - **Done**. Postgres Database backup cronjob has been configured in EKS cluster.
 - All relevant logs for all tiers need to be easily accessible (having them on the hosts is not an option).  
`Response` - Couldn't work on this task due to time constraint.
 - You should fork the repository and use it as the base for your system.  
`Response` - **Done**.
 - You should be able to deploy it on one larger Cloud provider: AWS/Google Cloud/Azure/DigitalOcean/RackSpace.  
`Response` - **Done**. Deployed on AWS Cloud.
 - The system should present relevant historical metrics to spot and debug bottlenecks.  
`Response` - **Done**. Prometheus and Grafana configured for metrics data collection and visualization to debug bottlenecks.
 - The system should implement CDN to allow content distribution based on client location.  
`Response` - **Done**. AWS CloudFront is configured as CDN.
