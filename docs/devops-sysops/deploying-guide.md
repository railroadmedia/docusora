# Deployment Guide

This guide provides a general overview of our server infrastructure, and a detailed guide about how to deploy changes 
to all of our environments. It also includes information about where to look for potential post-deployment 
issues and what to do if things go wrong.

## Our Server Infrastructure

All of our systems are inside AWS. Here is a list of AWS services we use primarily:
- EC2 (for our actual web servers which are managed by kuebernetes)
- RDS (for our mysql databases)
- Elasticache (for our redis databases)
- OpsWorks (for our older legacy websites)
- S3 (data and asset storage)
- Cloudfront (asset CDN)
- Codebuild & Amazon Container Services (for deploying, building, and storing our docker images)

<br>
  
The core of our system is powered by Kubernetes. We use a tool called 'kops' to manage our kubernetes clusters on EC2.
Our images which kubernetes uses to host our websites have the following software:
- PHP and Apache on the lowest brand/website level
- Cluster level ingress uses nginx
- EC2 load balancers as our front-line ingress endpoints

<br>

We use cloudfront as our DNS provider, front-line security service, and CDN/caching service.

<br>

The life of a request to one of our websites:

1. **Request Sent From The Client ->** 
1. **Cloudfront DNS**
   - Sends the request to the configured domain for that brands domain, in our case its an EC2 load balancer endpoint
1. **Kubernetes Cluster Ingress (nginx)**
   - The EC2 load balancer sends the request to one of the ec2 instances (which are the kubernetes nodes).
   - The nginx ingress running on each node determines which pod to send the request to based on the k8 config.
1. **A Kubernetes Pod/Deployment (which is our built docker image)**
   - Apache & PHP are the installed software in the pods. Apache is only used to terminate the SSL and 
     send the request to the PHP processes running in the pod.
1. **Our PHP/Laravel Application**
   - Processes the request and returns a response to the client.
    
Typically when something goes wrong it's at the PHP/Laravel Application layer however things can go wrong at any point
in the requests' path through our system.