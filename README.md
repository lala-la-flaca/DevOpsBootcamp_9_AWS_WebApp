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

   <img src="" width=800 />
  
3. Enter a Name and create a New Tag.

   <img src="" width=800 />
  
   
5. Select the AWS Amazon Linux image.
   
   <img src="" width=800 />
  
7. Choose the t2.micro instance type.
   
   <img src="" width=800 />
  
9. Under Key Pair Login, create a new Key Pair.
    
   <img src="" width=800 />
  
11. Enter a Key Pair Name, select the RSA type, and choose the .pem format for Linux. Click Create Key Pair.
    
   <img src="" width=800 />
  
13. Save the pem file in a secure location.
    
   <img src="" width=800 />
  
15. Add a Security Group, name it security-group-docker-server, and configure inbound rules to allow SSH access on port 22 from a specified source IP.
    
   <img src="" width=800 />
  
17. The instance has been created.
    
   <img src="" width=800 />
  
   
### Installing Docker on EC2
1. Copy the .pem file to the ~/.ssh folder in Linux, as it contains the key to access AWS.

   ```bash
   
   ```
   
3. Modify .pem file permissions to grant read-only access to the user.
   
   ```bash
   
   ```
   
5. Connect to the EC2 instance via SSH using the .pem file.
   
   ```bash
   
   ```
   
7. Update the package manager on the EC2 instance.
   
   ```bash
   
   ```
   
9. Install Docker.
    
   ```bash
   
   ```
   
11. Verify the Docker version.
    
   ```bash
   
   ```
   
13. Start the Docker daemon.
    
   ```bash
   
   ```
   
15. Add the current user to the Docker group to eliminate the need for sudo when running Docker commands, then reset the connection.
    
   ```bash
   
   ```
   
   

### Deploying Web Application
1. Run docker login to authenticate with the DockerHub repository.
   
   ```bash
   
   ```
   <img src="" width=800 />
   
3. Pull the application image from the repository using docker pull <repository/image-name>.
   
   ```bash
   
   ```
   <img src="" width=800 />
   
5. Verify that the Docker image is available on the EC2 instance using Docker images.
   
   ```bash
   
   ```
   
7. Run the image in detached mode using docker run -d -p 3000:3000 <image-name>.
   
   ```bash
   
   ```
   <img src="" width=800 />
   
9. Check that the container is running using docker ps.
    
   ```bash
   
   ```
   <img src="" width=800 />
   
11. Modify the inbound security group to allow access to port 3000 for the application:
a) Navigate to the EC2 instance.
b) Select the instance and click on the Security tab.
c) Click on the Security Group, then edit the Inbound Rules.
d) Add port 3000, allowing access from anywhere.
    
   <img src="" width=800 />
   
13. Open a browser and navigate to http://<EC2-IP>:3000 to access the application.
    

    [Web Application](http://13.59.163.202:3000/)
  
  
    <img src="" width=800 />


   
