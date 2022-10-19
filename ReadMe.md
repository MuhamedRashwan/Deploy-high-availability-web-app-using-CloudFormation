# Introduction
In this project, We’ll deploy web servers for a highly available web app using CloudFormation. We will write the code that creates and deploys the infrastructure and application for an Instagram-like app from the ground up. We will begin with deploying the networking components, followed by servers, security roles and software. 

# Project Requirements

## Server specs
We'll need to create a Launch Configuration for application servers in order to deploy four servers, two located in each of private subnets. The launch configuration will be used by an auto-scaling group.
We'll need two vCPUs and at least 4GB of RAM. The Operating System to be used is Ubuntu 18. So, We will choose an Instance size and Machine Image (AMI) that best fits this spec. 

## Security Groups and Roles
1. Since we will be downloading the application archive from an S3 Bucket, we'll need to create an IAM Role that allows your instances to use the S3 Service.

2. Udagram communicates on the default HTTP Port: 80, so our servers will need this inbound port open since we will use it with the Load Balancer and the Load Balancer Health Check. As for outbound, the servers will need unrestricted internet access to be able to download and update their software.

3. The load balancer should allow all public traffic (0.0.0.0/0) on port 80 inbound, which is the default HTTP port. Outbound, it will only be using port 80 to reach the internal servers.

4. The application needs to be deployed into private subnets with a Load Balancer located in a public subnet.

5. One of the output exports of the CloudFormation script should be the public URL of the LoadBalancer. 


