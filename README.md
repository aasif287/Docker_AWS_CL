# Using Docker at AWS with Command Line Interface

## Introduction
This project provides instructions for setting up and utilizing Docker on an Amazon Web Services (AWS) EC2 Linux server using the command line interface (CLI). Docker is a powerful tool for containerizing applications, enabling easier deployment and management.

## Tasks Overview
The following tasks are outlined to guide you through the process:

1. **Launch an AWS Server**: Launch an EC2 Linux server on AWS.
2. **Connect to AWS & Install Docker**: Connect to the server and install Docker.
3. **Verify Docker, Help, and Permissions**: Verify Docker installation, check help documentation, and manage permissions.
4. **Manage Docker Images**: Pull, list, and remove Docker images.
5. **Manage Docker Containers**: Create, start, stop, and remove Docker containers.

## Task Details

### Task 1: Launch an AWS Server
To start using Docker on AWS, you need to launch an EC2 Linux server. Follow these steps:
- Sign in to AWS (aws.amazon.com).
- Launch an EC2 instance with Linux.

### Task 2: Connect to AWS & Install Docker
Once your server is running, connect to it and install Docker.
```
mv /Downloads/docker-server.pem /keys
cd keys
ls
sudo chmod 400 ./docker-server.pem
ssh -i /home/rhyme/keys/docker-server.pem ec2-user@xx.xx.xxxx
sudo yum install -y docker
docker -v
exit
```

### Task 3: Verify Docker, Help, and Permissions
After installing Docker, verify its installation, check the help documentation, and manage permissions.
```
ssh -i /home/rhyme/keys/docker-server.pem ec2-user@xx.xx.xx.xx
docker -v
sudo service docker start
docker --help
docker container --help
sudo groupadd docker (it probably already exists)
sudo usermod -aG docker ec2-user
exit
ssh -i /home/rhyme/keys/docker-server.pem ec2-user@xx.xx.xx.xx
docker run hello-world
exit
```

### Task 4: Manage Docker Images
Learn how to pull, list, and remove Docker images.
```
sudo service docker start
ssh -i /home/rhyme/keys/docker-server.pem ec2-user@xx.xx.xx.xx
docker image pull httpd
docker image pull nginx:latest
docker image ls
docker image rm nginx:latest
docker image ls
exit
```

### Task 5: Manage Docker Containers
Explore creating, starting, stopping, and removing Docker containers.
```
sudo service docker start
ssh -i /home/rhyme/keys/docker-server.pem ec2-user@xx.xx.xx.xx
docker container ls -a
docker container create -it --name myalpine alpine:latest
docker container create -it -P docker container 5001:5000 --name mynginx nginx:latest
docker container stop myalpine
docker container ls
docker container rm myalpine
exit
```
By following these tasks, you'll be able to efficiently utilize Docker on an AWS EC2 Linux server through the command line interface.
