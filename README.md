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