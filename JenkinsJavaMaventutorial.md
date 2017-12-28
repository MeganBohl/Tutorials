* switched network setting to bridged adapter- wifi
    - SSH into VM from terminal


## Install Git:
`sudo yum install git`
`git --version`
 
`git config --global user.name "Your Name"`
`git config --global user.email "you@example.com"`

- check configs:
 
`git config --list`

## Install Docker:
https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-centos-7
`curl -fsSL https://get.docker.com/ | sh`
- start docker daemon:`sudo systemctl start docker`
- verfify running: `sudo systemctl status docker`
- ensure start at reboot: `sudo systemctl enable docker`
- add your username to the doccker group: `sudo usermod -aG docker $(whoami)`
    - OR `sudo usermod -aG docker username`
    - reboot

## Install  maven: `wget http://mirror.metrocast.net/apache/maven/maven-3/3.5.2/source/apache-maven-3.5.2-src.tar.gz`

## 
THEN,
 
Assuming you have installed Jenkins and set up the plug-ins, We would start at:

Fork and clone the sample repository on GitHub
https://jenkins.io/doc/tutorials/building-a-java-app-with-maven/

# Building a java app with Maven 
---
```docker run \
  --rm \
  -u root \
  -p 8080:8080 \
  -v jenkins-data:/var/jenkins_home \
  -v /var/run/docker.sock:/var/run/docker.sock \
  -v "$HOME":/home \
  jenkinsci/blueocean```

`https://spring.io/guides/gs/maven/`



