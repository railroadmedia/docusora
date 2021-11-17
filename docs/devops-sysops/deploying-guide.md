# Deployment Guide

This guide provides a general overview of our server infrastructure, and a detailed guide about how to deploy changes 
to all of our environments. It also includes information about where to look for potential post-deployment 
issues and what to do if things go wrong.

<br>

## Our Server Infrastructure

Nearly all of our systems are inside AWS. Here is a list of the primary AWS services we use:
- EC2 (for our actual web servers which are managed by kuebernetes)
- RDS (for our mysql databases)
- Elasticache (for our redis databases)
- OpsWorks (for our older legacy websites)
- S3 (data and asset storage)
- Cloudfront (asset CDN)
- Codebuild & Amazon Container Services (for deploying, building, and storing our docker images)

<br>
  
The webserver element of our backend system is built with Kubernetes. We use a cli tool called 'kops' to manage our 
kubernetes clusters on EC2.
Our docker images which kubernetes uses to host our websites have the following software:
- PHP and Apache on the lowest brand/website level
- Cluster level ingress uses nginx
- EC2 load balancers as our front-line ingress endpoints

<br>

We use cloudfront as our DNS provider, front-line security service (and ddos mitigation), and CDN/caching service.

<br>

The life of a request to one of our websites:

1. **Request Sent From The Client ->** 
1. **Cloudfront DNS**
   - Sends the request to the configured URI for that brands domain, in our case it's an EC2 load balancer endpoint.
1. **Kubernetes Cluster Ingress (nginx)**
   - The EC2 load balancer sends the request to one of the EC2 instances (which are the kubernetes nodes).
   - nginx running on each node (the ingress) determines which pod to send the request to based on the k8 config.
1. **A Kubernetes Pod/Deployment (which is our built docker image)**
   - Apache & PHP are the installed software in the pods. Apache is only used to terminate the SSL and 
     send the request to the PHP processes running in the pod.
1. **Our PHP/Laravel Application**
   - Processes the request and returns a response to the client.
    
Typically, when something goes wrong it's at the PHP/Laravel Application layer however things can go wrong at any point
in the requests' path through our system.

<br>

## Logs & Common Malfunction Areas

### Outage Alerting
We use a service called Pingdom to monitor our websites main pages every 30 seconds. This service sends out an alerts if
any of our websites start returning an error. This monitoring only reports for the public home pages, it will not catch
outages that only affect the members' area.  

Alerts will automatically be emailed to some team members and also be posted in the 'dev-uptime-reporting' slack.

<br>

### Kibana & Logs
Our kubernetes pods report all their software logs (PHP/Apache/nginx) to our Kibana/Elastic Search cluster running 
on a hosted cloud service called logit.io. Log in credentials should be in 1pass.

[Logit.io Dashboard](https://dashboard.logit.io/a/f60c21b4-781c-4c1a-ac70-1c906af3ad55)  
[Logit.io Kibana Direct Link](https://dashboard.logit.io/a/f60c21b4-781c-4c1a-ac70-1c906af3ad55/s/993f2ebf-75ae-490c-9bd4-c0ebd7141b8f/kibana/access)

To see a general error list click 'Open' in the top right to select a saved search. Use the 'General Error' saved search.
You can choose a relative time to show logs from. The last 4 hours is a common report. When something is going wrong 
that is affecting users it will almost always cause some kind of error reporting in Kibana.

<br>

### Database Overload
A common source of problems is an overload in our mysql database servers. We use AWS Aurora (MySQL version) to host 
our main databases. Team members with access can monitor database usage and stats here:

[AWS Aurora Cluster][https://us-east-2.console.aws.amazon.com/rds/home?region=us-east-2#database:id=rescue-snap-restore-cluster;is-cluster=true;tab=connectivity]

The Performance Insights tool is very useful for finding queries that are using large amounts of CPU. Choose 
'Performance Insights' from the sidebar in the AWS Aurora area and choose the 'rescue-snap-restore' instance. Choose 
'Slice By SQL' from the drop down menu near the stats to see which queries are the problem.

<br>

### Deployment or K8 Pod Failure
Sometimes something will go wrong with the kubernetes pods and their deployment process. You can view any brands pods
in our local dev manager environment with the 'r' tool.

1. Set your local cli k8 namespace to the right brand with the following commands: ```kset``` -> choose brand -> choose environment (likely production)
2. Run: ```k get pods```
3. If you see any pods with a failed Status or many Restarts, something is probably going wrong. You can watch a 
   specific pods logs in real time from the cli using: ```k logs -f NAME```. For example: 
   ``` k logs -f drumeo-production-deployment-755fb77d8c-2kzfv```

<br>

### Quickly Reverting Deployments
When you deploy, a new docker image is generated, and our deployment tool tells our k8 cluster to switch that brands 
pods to the new image. 
New pods are spun up using the new docker image. Once they are running, the existing pods are terminated.  

If a deployment happens and it starts causing problem such as an outage, mass new errors in the logs, or a database 
overload, you can tell the k8 cluster to quickly switch the brand back to its previous images using these commands:

1. Set your local cli k8 namespace to the right brand with the following commands: ```kset``` -> choose brand -> choose environment (likely production)
2. ```k rollout undo deployment/BRAND-production-deployment``` 
   for example ```k rollout undo deployment/drumeo-production-deployment```
   
NOTE: This will not solve issues if they are related to database migrations. Once a migration is deployed, 
and it updates the database schema, reverting the deployment will not revert the migration.  

Once you have reverted a deployment, keep in mind if you deploy again k8 will still build the docker image based on 
the latest git branch state so you may also need to revert the relevant commits until the issue is resolved.

<br>

## How To Deploy
To deploy your must have our local 'railenvironment' set up on your machine. Our 'r' tool from the manager docker 
container is used for deployment.

1. ```r deploy BRAND```
2. Choose the environment you wish to deploy. Production is always the brand git repo master branch. 
   Staging is the staging branch.
3. Wait for the image to build and deploy. You will get a success or failure message. 
   Deployment typically takes 5-10 minutes.
4. Once your CLI finished the build and gives you a success message keep in mind that the new docker images still have 
   to propagate among the k8 pods. This can take 3-10 minutes. You may not see changes on the production sites until
   5-10 minutes after deployment. You can check the state of the pod image propagation with ```k get pods```
5. Always double-check the production websites to make sure your changes were deployed successfully and are not causing
   problems for users.
6. If you deployed backend changes, please monitor our server logs in Kibana for a few minutes to make sure nothing
   is going wrong after the deployment was complete. (See [Kibana & Logs](#kibana--logs) section above).

#### Publishing Vuesora
1. To publish a staging version (for testing): 
  - merge the feature branch into staging
  - run `git status` to make sure you git directory is clean
  - run `./prerelease.sh` (this will create a staging release of Vuesora for testing)
  - Once the published, you can install in the staging branch of the respective environment with `yarn add vuesora@staging`
3. Once feature branch has been tested in staging, merge feature branch into the release branch.
  - Current branch is `0.17-`
4. In release branch, make sure your local git directory is clean, and run `./publish.sh`.
  - If you have changes that have not been commited, publish script will throw an error.
5. Once your new version of Vuesora is published, you will be able to install in the respective environments with `yarn add vuesora@latest`.
