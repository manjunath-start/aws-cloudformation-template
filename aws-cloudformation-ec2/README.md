# AWS CloudFormation Template for EC2, ALB, and VPC

This repository contains an AWS CloudFormation template (`cloudformation.yaml`) to deploy an infrastructure setup with:
- A VPC with public and private subnets.
- An EC2 instance acting as a web server.
- A jump server for secure SSH access.
- An Application Load Balancer (ALB) to handle HTTP traffic.
- Security groups to control network access.
- A NAT Gateway for private subnet internet access.

## Features
- Automates the deployment of a secure, scalable web server.
- Uses an ALB to distribute incoming traffic.
- Supports SSH access through a bastion (jump) server.
- Implements a NAT Gateway to provide internet access to private instances.

## Prerequisites
- An AWS account.
- AWS CLI installed and configured.
- CloudFormation permissions to create resources.

## Deployment Instructions
1. **Clone this repository:**
   ```sh
   git clone https://github.com/your-username/aws-cloudformation-ec2.git
   cd aws-cloudformation-ec2

2. **Deploy the CloudFormation stack:**
   ```sh
   aws cloudformation create-stack --stack-name my-ec2-stack --template-body file://cloudformation.yaml --capabilities CAPABILITY_NAMED_IAM

3. **Check the status:**
   ```sh
   aws cloudformation describe-stacks --stack-name my-ec2-stack

4. **Access the Web Server:**
   **Retrieve the ALB DNS:**
   ```sh
   aws cloudformation describe-stacks --stack-name my-ec2-stack --query "Stacks[0].Outputs[?OutputKey=='LoadBalancerDNS'].OutputValue" --output text

   **Open the ALB DNS in a browser to check if the web server is running.**

5. **Cleanup**
   **To delete the CloudFormation stack and all associated resources:**
   ```sh
   aws cloudformation delete-stack --stack-name my-ec2-stack
