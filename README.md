# <img src="https://github.com/user-attachments/assets/56192d5e-c2a7-4584-8b58-d6c8951e2ae4" width="250" /> Deploying Web Application on EC2

## Description

This demo project is part of **Module 9**: **AWS Services** from **Nana DevOps Bootcamp**. This project involves deploying a web application manually on an AWS EC2 instance. The deployment process includes setting up the EC2 instance, installing Docker, and deploying a Docker image from a private Docker repository. <br />


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

### Creating an AWS Admin account
1. Create an AWS account using a root user.
   
2. Create an admin user using the IAM service.
   
   <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_7_docker_ECR/blob/main/Img/Creating%20Admin%20User%202.png" width=800 />
   
3. Assign admin privileges.

   <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_7_docker_ECR/blob/main/Img/providing%20administrator%20privileges.png" width=800 />

4. Sign out from the root user.
   
5. Sign in using the admin user account.
   
### Creating an EC2 Instance
1. Navigate to EC2 and click on Launch Instance.

   <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_9_AWS_WebApp/blob/main/Img/1%20launch%20instance.PNG" width=800 />
  
2. Enter a Name and create a New Tag.

   <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_9_AWS_WebApp/blob/main/Img/1%20Creating%20EC2%20a.png" width=800 />
  
3. Select the AWS Amazon Linux image.
   
4. Choose the t2.micro instance type.
   
   <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_9_AWS_WebApp/blob/main/Img/1%20Creating%20EC2%20b.png" width=800 />
  
5. Under Key Pair Login, create a new Key Pair.
    
6. Enter a Key Pair Name, select the RSA type, and choose the .pem format for Linux. Click Create Key Pair.
    
   <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_9_AWS_WebApp/blob/main/Img/1%20Creating%20EC2%20c%20.png" width=800 />
  
7. Save the pem file in a secure location.
  
8. Add a Security Group, name it security-group-docker-server, and configure inbound rules to allow SSH access on port 22 from a specified source IP.

   <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_9_AWS_WebApp/blob/main/Img/1%20Creating%20EC2%20d.png" width=800 />
   
9. The instance has been created.

   <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_9_AWS_WebApp/blob/main/Img/1%20instance%20created.PNG" width=800 />
  
   
### Installing Docker on EC2
1. Copy the .pem file to the ~/.ssh folder in Linux, as it contains the key to access AWS.

   ```bash
     mv docker-server.pem ~/.ssh
   ```
   
2. Modify .pem file permissions to grant read-only access to the owner.
   
   ```bash
     chmod 400 docker-server.pem 
   ```
   <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_9_AWS_WebApp/blob/main/Img/2%20changing%20permision%20to%20pem%20file.PNG" width=800 />
   
3. Connect to the EC2 instance via SSH using the .pem file.
   
   ```bash
     ssh -i ~/.ssh/docker-server.pem ec2-user@13.59.163.202
   ```
   
   <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_9_AWS_WebApp/blob/main/Img/SSH%20ec2.png" width=800 />
   
4. Update the package manager on the EC2 instance.
   
   ```bash
     sudo yum update
   ```
   <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_9_AWS_WebApp/blob/main/Img/4%20updating%20package%20maneger.png" width=800 />
   
5. Install Docker.
    
   ```bash
   sudo yum install docker
   ```
   
   <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_9_AWS_WebApp/blob/main/Img/5%20Installing%20docker.png" width=800 />
   
6. Verify the Docker version.
    
   ```bash
     docker --version
   ```
   
     <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_9_AWS_WebApp/blob/main/Img/6%20docker%20is%20available.png" width=800 />
     
7. Start the Docker daemon.
    
   ```bash
     sudo service docker start
   ```

   <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_9_AWS_WebApp/blob/main/Img/8%20Starting%20docker%20daemon.png" width=800 />
   
9. Verify that the Daemon is running

    ```bash
      ps aux | grep docker
    ```
    
    <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_9_AWS_WebApp/blob/main/Img/9%20Checking%20tha%20docker%20is%20running%20dockerd.png" width=800 />
    
10. Add the current user to the Docker group to eliminate the need for sudo when running Docker commands, then reset the connection.
    
   ```bash
     sudo usermod -aG docker $USER
   ```

   <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_9_AWS_WebApp/blob/main/Img/10%20Adding%20user%20to%20docker%20group.png" width=800 />
   

### Deploying Web Application
1. Run docker login to authenticate with the DockerHub repository.
   
   ```bash
     docker login
   ```
   <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_9_AWS_WebApp/blob/main/Img/14%20Login%20docker%20repository%20from%20ec2.png" width=800 />
   
2. Pull the application image from the repository using docker pull <repository/image-name>.
   
   ```bash
     docker pull lala011/demo-app:web-app-1.0
   ```
   <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_9_AWS_WebApp/blob/main/Img/15%20Pulling%20Image%20from%20dockerhub%20provate%20repo%20ec2.png" width=800 />
   
3. Verify that the Docker image is available on the EC2 instance using Docker images.
   
   ```bash
     docker images
   ```
   
   <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_9_AWS_WebApp/blob/main/Img/16%20Img%20available%20in%20EC2.png" width=800 />
   
4. Run the image in detached mode using docker run -d -p 3000:3080 <image-name>.
   
   ```bash
     docker run \
     -d \
     -p 3000:3080 \
     lala011/demo-app:web-app-1.0
   ```
   
   <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_9_AWS_WebApp/blob/main/Img/17%20RunningAppContainer.png" width=800 />
   
5. Check that the container is running using docker ps.
    
   ```bash
   docker ps
   ```
   
   <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_9_AWS_WebApp/blob/main/Img/18%20Running%20cnatiner.png" width=800 />
   
6. Modify the inbound security group to allow access to port 3000 for the application:
   
   a) Navigate to the EC2 instance.
    
   b) Select the instance and click on the Security tab.
    
   c) Click on the Security Group, then edit the Inbound Rules.
    
   <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_9_AWS_WebApp/blob/main/Img/19%20Modifying%20Security%20group%20one.png" width=800 />
     
   d) Add port 3000, allowing access from anywhere.

   <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_9_AWS_WebApp/blob/main/Img/21%20Adding%20%20New%20inbound%20rule.PNG" width=800 />
    
8. Open a browser and navigate to http://<EC2-IP>:3000 to access the application.
    
    [Web Application](http://13.59.163.202:3000/)
  
  
    <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_9_AWS_WebApp/blob/main/Img/22%20WebApp%20running%20on%20port%203000%20on%20EC2.png" width=800 />


   
