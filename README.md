# GAME-DEPLOYMENT
Deploying the 2048 Game on Docker and Kubernetes with Jenkins CI/CD
## CREATE AN EC2 INSTANCE
1. Created and launched an EC2 instance using the Ubuntu 22.04 Image and T2x Large. 
Allocate a 25gig storage to the instance and enable public IP in the VPC settings.
![screen shot of my ubuntu version 22.04 running on jammy 64](./Images/ubuntu%20image.png)
Selected on launch instance in AWS to create my instance 
![Screenshot of how your instance should appear](./Images/Ec2%20instance.png)

2. connect to the instance by clicking on the instance and the connect to ssh 
[connect to your ec2 using the link](ssh -i "netflix_clone.pem" ubuntu@ec2-51-20-93-60.eu-north-1.compute.amazonaws.com)

3. a. login to root access with sudo su
    b. update your ubuntu os with `apt update`
    c. for the purpose of this project clone this repository to access the backend data (https://github.com/Aakibgithuber/Deploy-Netflix-Clone-on-Kubernetes)

** create an elastic ip on your instance**
[Image of elastic ip address](./Images/Screenshot%20(496).png)

**##STEP 2: set up docker and build images **
    a. apt-get install docker.io
    b. **usermod -aG docker $USER** # Replace with your username e.g ‘docker_admin’
    c. newgrp docker
    d. **sudo chmod 777 /var/run/docker.sock →** #is used to grant full read, write, and execute permissions to all users for the Docker socket file, which allows unrestricted access to the Docker daemon and is a significant security risk.

   **run the following commands to build and run docker container →**

    a. docker build -t netflix . Ensure your tag name is written in small letters otherwise it would not build 
     # Add Docker's official GPG key:
sudo apt-get update
sudo apt-get install ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc

# Add the repository to Apt sources:
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "$VERSION_CODENAME") jammy" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update

    b. docker run -d — name netflix -p 8081:80 netflix:latest → this maps the container port to your ec2 port

    c. go to your ec2 →security groups →open the port 8081 by adding rule custom tcp = 8081