# psdockerawsgs
##1. Docker on AWS: Getting Started
###3 Installing Docker on an EC2 Instance
```
uname -r
apt install apt-transport-https ca-certificates
apt-key adv --keyserver hkp://p80.pool.sks-keyservers.net:80 --recv-keys 58118E89F3A912897C070ADBF76221572C52609D
vim /etc/apt/sources.list.d/docker.list
```
edit (16.04)
```
deb https://apt.dockerproject.org/repo ubuntu-xenial main
```
then
```
apt update
apt install linux-image-extra-$(uname -r) linux-image-extra-virtual
apt update
apt install docker-engine
```


###4 Running Docker from the Command Line
```
sudo su
systemctl start docker
systemctl status docker
docker run hello-world
docker 
docker info
```

start interactive shell
```
docker run -it ubuntu bash
ls
apt update
exit
```

daemon
```
docker run -it --detach=true ubuntu bash
docker ps
docker rename oldname newname
docker ps
docker inspect newname | less
docker network ls
docker network create newnet
docker network inspect newnet | less
docker network connect newnet newname
docker inspect newname	
ping 172.18.0.2 [newnet]
ping 172.17.0.2	[bridge]
```
###5 Working with Dockerfiles
Dockerfile
```
FROM ubuntu:16.04

RUN apt update
RUN apt install -y apache2
RUN echo "test" > /var/www/html/index.html
EXPOSE 80
```

sudo su
docker build -t "webserver" .
docker images
docker run -d -p 80:80 webserver /usr/sbin/apache2ctl -D FOREGROUND
docker ps
curl localhost
from browser: 
ip
```

###6 Working with Docker Hub Images
```
docker search apache/ubuntu
docker search ubuntu
docker pull ubuntu-upstart
docker run -it ubuntu-upstart /bin/bash
```

##2. Amazon ECS: Exploring the Environment
###2 EC2 Container Service: Defining Terms
service->(initiate)->Task->(contains)->container


##3. Amazon ECS: Building a Cluster Environment
###1 Prepare an EC2 Instance and an ECS Task
####02:00
Role type: choose `Amazon EC2 Role for EC2 Container Service`  
Attach policy


####04:33
container name: mycontainer  
image: dbclinton/newserver  ->add  
next time we need to build a service to manage the task


###2 Build an EC2 Service to Run the Task
###3 Working with ECS Through the AWS CLI
install aws-cli
```
python --version
curl "https://s3.amazonaws.com/aws-cli/awscli-bundle.zip" -o "awscli-bundle.zip"
sudo apt install unzip
unzip awscli-bundle.zip
sudo ./awscli-bundle/install -i /usr/local/aws -b /usr/local/bin/aws
aws configure
<ul>add us-east-1</ul>
cd .aws
ls
nano config
```
ecs
```
aws ecs help
aws ecs list-clusters
aws ecs describe-clusters
aws ecs create-cluster --cluster-name newcluster
```

