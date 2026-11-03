# AWS-INSTANCE-ROLES
This repository documents the setup and verification of IAM Roles attached to Amazon EC2 instances. It illustrates how to grant virtual machines programmatic access to AWS services securely, following the principle of least privilege

First, connect to your EC2 instance through your management console. For this walkthrough, you can either use SSH or EC2 Instance Connect

<img width="1024" height="576" alt="image" src="https://github.com/user-attachments/assets/4ec78847-1b09-4f0d-9caa-b82944f6f5b1" />

Now I am on the Amazon Linux 2023 prompt

<img width="959" height="1080" alt="image" src="https://github.com/user-attachments/assets/05bf40f9-1690-4cc5-8088-d9e8c9d9496b" />

Here we can execute Linux commands such as "ping google.com"

<img width="966" height="1080" alt="image" src="https://github.com/user-attachments/assets/01d91aa6-6d82-4660-9b7a-1ed17366441e" />

One of the best parts about Amazon Linux 2023 is that the AWS CLI is ready to go right away; you can test it immediately by checking the version "aws --version". That said, API requests to IAM, such as "aws iam list-users", will fail without the required IAM permissions attached

Version command:

<img width="955" height="1080" alt="image" src="https://github.com/user-attachments/assets/a1600997-96d3-4704-ab8c-a77f92abcc27" />

