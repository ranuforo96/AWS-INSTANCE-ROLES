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

List users command:

<img width="967" height="1080" alt="image" src="https://github.com/user-attachments/assets/9421d5fe-8ddc-4ed9-a9d8-3044be8f5c3a" />

Running the list users command fails because the required credentials are missing. The error message then prompts you to run: aws login, in order to configure said credentials. However, this also fails because it attempts to launch a web browser on an EC2 instance operating without a GUI

<img width="961" height="1080" alt="image" src="https://github.com/user-attachments/assets/9964255a-7778-449b-9def-c7bf093bde60" />

Resolution: Assign an IAM role to the EC2 instance to manage permissions automatically

We do this by first opening the Amazon EC2 Console

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/07676eb8-f3d2-4791-966d-1099211f2a24" />

In the left navigation pane, select Instances

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/2ef92cde-5ddb-4e13-9e3b-ed5d303edb90" />

Select your target EC2 instance from the list: My First EC2

Before moving forward, I would like to highlight that there is currently no role assigned to the EC2

<img width="1024" height="495" alt="image" src="https://github.com/user-attachments/assets/d8e92198-e5b1-4963-b8b6-8b9c3fd43e12" />

Next, click the Actions dropdown menu at the top right, hover over Security, and select Modify IAM role

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/8566de4f-c584-4e54-9955-5885852d375f" />

Choose your desired IAM role from the IAM role dropdown list: DemoRoleForEC2. This role has IAMReadOnlyAccess permissions 

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/ad838d46-eb06-4926-a2e6-86c897765ee5" />

Click Update IAM role to apply the changes

<img width="909" height="1024" alt="image" src="https://github.com/user-attachments/assets/e87bb3b7-3aa1-4935-8824-5770826d0712" />

The role has now been successfully attached to the EC2

<img width="1024" height="576" alt="image" src="https://github.com/user-attachments/assets/5ff2fd70-ddb2-439a-bc36-8726a099ce07" />

To verify the changes were made, I can simply type the list command I tried running previously in the Amazon Linux 2023

<img width="967" height="1080" alt="image" src="https://github.com/user-attachments/assets/253b0b03-a710-44e4-bc33-46168e34ae57" />

The command now executes. However, in contrast, if we remove the permission from the IAM role, access will again be revoked

<img width="1024" height="576" alt="image" src="https://github.com/user-attachments/assets/1be86652-51b8-4afd-9f1d-dff44c70b621" />

Error message due to permission removal:

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/2859e94c-e6f9-4d73-8d9b-38e73c69133b" />

