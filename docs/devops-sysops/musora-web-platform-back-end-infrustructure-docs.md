# Deployment Guide

This guide provides a general overview of our server infrastructure, and a detailed guide about how to deploy changes 
to our musora web platform environment. It also includes information about where to look for potential post-deployment 
issues and what to do if things go wrong.

<br>

## Our Server Infrastructure

Our infrastructure is powered by Laravel Vapor. Vapor is essentially just a front-end management tool for various
AWS services. It uses AWS Lambda to process the http requests. Laravel Vapor has a powerful CLI tool which we use
to manage our infrastructure.

[Laravel Vapor Docs](https://docs.vapor.build/)

Here is a list of the primary AWS services we use:
- Lambda (for our actual web servers, managed by Laravel Vapor)
- RDS (for our mysql databases)
- SQS (for queue processing, managed by Laravel Vapor)
- Elasticache (for our redis databases)
- OpsWorks (for our older legacy websites)
- S3 (data and asset storage)
- Cloudfront (asset CDN)

<br>
  
The webserver element of our backend system uses a docker image hosted on AWS Lambda. Laravel Vapor handles the docker
image building and uploading.

<br>

We use cloudfront as our DNS provider, front-line security service (and ddos mitigation), and CDN/caching service.

<br>

The life of a request to one of our websites:

1. **Request Sent From The Client ->** 
1. **Cloudfront DNS ->**
   - Sends the request to the configured URI for that brands domain, in our case it's an endpoint created 
   by Vapor inside AWS using Route53.
1. **Our PHP/Laravel Application That is inside AWS Lambda**
   - Processes the request and returns a response to the client.
    
Typically, when something goes wrong it's at the PHP/Laravel Application layer.

<br>

## Logs & Common Malfunction Areas

### Outage Alerting
We use a service called Pingdom to monitor our websites main pages every 30 seconds. This service sends out an alerts if
any of our websites start returning an error. This monitoring only reports for the public home pages, it will not catch
outages that only affect the members' area.  

Alerts will automatically be emailed to some team members and also be posted in the 'dev-uptime-reporting' slack.

<br>

### Logs
Our server logs (HTTP/Queue/CLI) are managed by Laravel Vapor and are stored inside AWS Cloudwatch. 
They can be accessed inside the Laravel Vapor dashboard under 
Projects -> (choose project) -> (choose environment) -> Logs.

<br>

### Database Overload
A common source of problems is an overload in our mysql database servers. We use AWS Aurora (MySQL version) to host 
our main databases. Team members with access can monitor database usage and stats here:

[AWS Aurora Cluster][https://us-east-2.console.aws.amazon.com/rds/home?region=us-east-2#database:id=rescue-snap-restore-cluster;is-cluster=true;tab=connectivity]

The Performance Insights tool is very useful for finding queries that are using large amounts of CPU. Choose 
'Performance Insights' from the sidebar in the AWS Aurora area and choose the 'rescue-snap-restore' instance. Choose 
'Slice By SQL' from the drop down menu near the stats to see which queries are the problem.