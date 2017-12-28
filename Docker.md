-  *image* is a lightweight, stand-alone, executable package that includes everything needed to run a piece of software, including the code, a runtime, libraries, environment variables, and config files.
- *container* is a runtime instance of an image—what the image becomes in memory when actually executed. It runs completely isolated from the host environment by default, only accessing host files and ports if configured to do so.

-  TRY TUTORIAL LATER: https://docs.docker.com/get-started/ 

## Install Docker:
https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-centos-7
`curl -fsSL https://get.docker.com/ | sh`
- start docker daemon:`sudo systemctl start docker`
- verfify running: `sudo systemctl status docker`
- ensure start at reboot: `sudo systemctl enable docker`
- `sudo chkconfig docker on`
- add your username to the doccker group: `sudo usermod -aG docker $(whoami)`
    - OR `sudo usermod -aG docker username`
    - reboot

docker |more

`sudo systemctl start docker`
** Test to see if running:
`sudo docker run hello-world`

#  Install Docker Compose
`sudo yum install python-pip`
`yum install docker-compose`
`mkdir hello-world`
`cd hello-world`
`nano docker-compose.yml`

`my-test:
  image: hello-world`

** Creates Container:
`docker-compose up`
---

### CentOS Docker LAMP
https://github.com/wrender/centos-docker-lamp
`docker run -d -p 8080:80 -p 8443:443 -p 8022:22 -t otherdata/centos-docker-lamp:latest`


/Users/meganbohl/VirtualBox VMs/CentosMinimalJenkins12-6-17Clone/CentosMinimalJenkins12-6-17Clone.vdi

/Users/meganbohl/VirtualBox VMs/CentosMinimalJenkins12-6-17Clone/CentosMinimalJenkins12-6-17Clone.vdi

https://www.cyberciti.biz/faq/kill-process-in-linux-or-terminate-a-process-in-unix-or-linux-systems/

/dev/sda2 

---

###DOCKER APACHE CENTOS
- Install with: `docker run -dit --name my-apache-app -p 8080:80 -v "$PWD":/usr/local/apache2/htdocs/ httpd:2.4`
`docker exec -it my-apache-app /bin/bash`
`docker cp index.html my-apache-app:/`
`docker exec -it my-apache-app /bin/bash`
`cp index.html /usr/local/apache2/htdocs/`
`cd /usr/local/apache2/htdocs/`
`ls -al`
`chmod 644 index.html`
- test localhost:8080



