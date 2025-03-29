# <img src="https://github.com/user-attachments/assets/56192d5e-c2a7-4584-8b58-d6c8951e2ae4" width="250" /> Deploying Web Application on EC2
## Description

This demo project is part of Module 9: AWS Services from Nana DevOps Bootcamp. This project involves deploying a web application manually on an AWS EC2 instance. The deployment process includes setting up the EC2 instance, installing Docker, and deploying a Docker image from a private Docker repository. <br />


## 🚀 Technologies Used

- <b>Docker: Docker for containerization.</b>
- <b>AWS EC2: Cloud provider for hosting WebApp.</b>
- <b>Linux: Ubuntu for Server configuration and management.</b>
- <b>DockerHub: Private docker repository.</b>

  

## 🎯 Features

- <b>Create and Configure an EC2 instance on AWS</b>
- <b>Install Docker on EC2.</b>
- <b>Deploy docker image from DockerHub repository.</b>


## 🏗 Project Architecture

<img src=""/>


## ⚙️ Project Configuration:

### Creating an AWS Admin Account
### Create an AWS account
1. Create an AWS account using a root user.
   
2. Create an admin user using IAM service.
   
   <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_7_docker_ECR/blob/main/Img/Creating%20Admin%20User%202.png" width=800 />
   
3. Assign admin privileges.

   <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_7_docker_ECR/blob/main/Img/providing%20administrator%20privileges.png" width=800 />

4. Sign out from the root user.
5. Sign in using the admin user account.
   
### Creating an EC2 Instance
1. Navigate to EC2 and click on Launch Instance.
2. Add a Name and a New Tag.
3. Select the AWS Amazon Linux Image
4. Select the instance type t2.micro.
5. In the key pair login , create a Key pair login
6. Add a key pair name, select the RSA type and use .pem file format if you are working with linux, create the Key pair.
7. Add a security group, and named security-group docker-server, add the inboud rules to allow SSH access port 22, and source IP.
8. The instance hs ben created.

### Installing Docker on EC2
1. Copy the .pem file to the .ssh Linux folder as the .pem file contains the key to access AWS.
2. Change the rights of the file to only provide read access to the user.
3. SSH to EC2 providing the .PEM file as input.
4. Update the package manager of the EC2
5. Install Docker
6. Verify the Docker version
7. Start the Docker daemon.
8. Add the current user to the docker group to avoid using the sudo every time a docker command I used and reset the connection.
   

### Deploying Web Application
1. Run docker login to login to the DockerHub repository
2. Pull the App image from the Repository using docker pull.
3. Verify that the docker image is available on the EC2
4. Run the image in a detach mode
5. Check that the container is running.
6. Modify the inbound security group to allow access to port 3000 for the application, and navigate to the instance.
7. Select the instance and click on the security tab.
8. Click on the security group and edit the inbound rules.
9. Add port 3000 to have access from everywhere.
10. Open a browser and navigate to EC2 IP address:3000


   
