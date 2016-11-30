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
