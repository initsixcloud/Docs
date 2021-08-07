# Install and Configure Maven, git & Docker in Jenkins server

## Install Maven
```sh
yum install wget
wget http://apachemirror.wuchna.com/maven/maven-3/3.6.3/binaries/apache-maven-3.6.3-bin.tar.gz
tar -xvzf apache-maven-3.6.3-bin.tar.gz
export M2_HOME=/opt/apache-maven-3.6.3
export M2=$M2_HOME/bin
PATH=$PATH:$M2
# To set it permanently update your .bash_profile
source ~/.bash_profile
```

## Install git
yum install git


## Install Docker
```sh
yum install docker
systemctl start docker
systemctl enable docker
```

## Assign shell to jenkins user

```sh
vi /etc/passwd
change shell from /bin/false to /bin/bash
```

## provide permissions to jenkins user in jenkins server to access docker
```sh
  sudo groupadd docker
  sudo usermod -aG docker jenkins
  sudo chmod 777 /var/run/docker.sock
```
