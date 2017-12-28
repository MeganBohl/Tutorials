## Move AWS Devopsclass.pem SSH key to .ssh dir)

`ssh -i "MeganAWS.pem" ec2-user@meganaws.mywire.org -p 22`
*at each login, cd to .ssh to make sure ssh file is visible

---
## Initial Set up

-  Be sure to set up SSH in security groups and allow SSH from any IP
- add HTTP or HTTPS for inbounds in security groups if wanting to allow web access


`cd Downloads`
`ls`
`MeganAWS.pem`
`cp MeganAWS.pem ~/.ssh`
`cd ~`
`ls -a`
`cd .ssh`
`ls`

- shows: DevOpsClass.pem	id_rsa		id_rsa.pub	known_hosts
Megans-MacBook-Pro:.ssh meganbohl$ `ls -al`
total 32
drwx------   6 meganbohl  staff   192 Nov 10 09:06 .
drwxr-xr-x+ 54 meganbohl  staff  1728 Nov  7 09:06 ..
-rw-r--r--@  1 meganbohl  staff  1692 Nov 10 09:06 DevOpsClass.pem  ***NOT SAFE- Everyone can read the private key**
-rw-------   1 meganbohl  staff  1675 Oct 10 09:22 id_rsa
-rw-r--r--   1 meganbohl  staff   416 Oct 10 09:22 id_rsa.pub
-rw-r--r--   1 meganbohl  staff  1986 Nov 10 09:36 known_hosts
Megans-MacBook-Pro:.ssh meganbohl$ 



### SSH to instance
-  Change private key file permissions so they are no longer public: 
    `chmod 400 DevOpsClass.pem`  
- ssh to instance: `ssh -i "DevOpsClass.pem" `ec2-user@ec2-34-213-240-151.us-west-2.compute.amazonaws.com`


---



# SCREENSHOT FROM ADDING DAVID AS USER
```[ec2-user@ip-172-31-29-46 ~]$ sudo adduser dprince
[ec2-user@ip-172-31-29-46 ~]$ sudo passwd dprince
Changing password for user dprince.
New password: 
Retype new password: 
passwd: all authentication tokens updated successfully.

[ec2-user@ip-172-31-29-46 ~]$ sudo gpasswd -a dprince wheel
Adding user dprince to group wheel


[dprince@ip-172-31-29-46 ~]$ ssh-keygen
Generating public/private rsa key pair.
Enter file in which to save the key (/home/dprince/.ssh/id_rsa): 
Created directory '/home/dprince/.ssh'.
Enter passphrase (empty for no passphrase): 
Enter same passphrase again: 
Your identification has been saved in /home/dprince/.ssh/id_rsa.
Your public key has been saved in /home/dprince/.ssh/id_rsa.pub.
The key fingerprint is:
SHA256:ECcwLFmtDIiYuyLzYvqmY6VmdWorJJlh9JkMgpjh/g0 dprince@ip-172-31-29-46.us-west-2.compute.internal
The key's randomart image is:
+---[RSA 2048]----+
|*= ++oo .        |
|@o+ ...+         |
|oo++o..          |
|+. =o  .         |
|.* E    S        |
|O..oo.           |
|=o+.o.           |
|oBoo             |
|O*+..            |
+----[SHA256]-----+
[dprince@ip-172-31-29-46 ~]$ cd .ssh
[dprince@ip-172-31-29-46 .ssh]$ ls
id_rsa  id_rsa.pub
[dprince@ip-172-31-29-46 .ssh]$ ls
id_rsa  id_rsa.pub
[dprince@ip-172-31-29-46 .ssh]$ cat id_rsa.pub
ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDU8eJHYUFuozOF2yHL3Vycd6Nt0Aa9nm4u7BiI5RE0A/6EmPkFE4v4QE/3ahZh4LmRrnOnlIxnK2mEQb9t5FJ0Y+1hNlMx91bs6jwWZVD/2Rm2uAa6zQfjAvaeePUFM/geLfINz0nXmPhlpn+gG+hbwYBiaNNsEl/W3TtKBXCfKFfyeSyxTdPAKZ+jdIWguVFoTvAuWkKk5LrX4d2iQas3AP/Rt08nr6CJzfGbvixobIsNXXvd76X5o93v91Ydi9rbozssCDDBNsP1vKiYm2/TD0Er1L50KGJlDEGLKznS4+rrzHWv6kKvM3qK7KB2sMJfSYMD8ZODxsWYbmpxQTM3 dprince@ip-172-31-29-46.us-west-2.compute.internal
[dprince@ip-172-31-29-46 .ssh]$ sudo nano authorized_keys
[dprince@ip-172-31-29-46 .ssh]$ sudo chown dprince:dprince authorized_keys

cat id_rsa  (copied all)
went into .ssh in my mac
saved as dprince.private
chmod 700
ls -al to make sure permissions are correct

*Dont forget: COPY SSH FROM FIRST DASH (-) TO LAST DASH*```



# ADD NEW USER and SSH http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/managing-users.html
`sudo adduser newuser`
`sudo passwd newuser`
`gpasswd -a newuser wheel`
`sudo su - newuser`
`ssh-keygen`
 `mkdir .ssh` (if not already made)
    `touch .ssh/authorized_keys`
        `ls -al`
    `chmod 700 authorized_keys`
        `ls -al`
        `cat id_rsa.pub`
        - copy and paste public key from "SSH-RSA to beginning of next prompt"
`sudo nano authorized_keys`
- changing owner from root to newuser: `sudo chown newuser:newuser authorized_keys`

- Get the private key to the new user: copy the entire private key COPY SSH FROM FIRST DASH (-) TO LAST DASH *------BEGIN RSA PRIVATE KEY fjdkajdfkajfkjakfjalkfjs ------END RSA PRIVATE KEY -----*

- open new terminal on local machine
`ls -al`
- verify .ssh exists 
`cd .ssh`
- create file for private key: `nano newuser.private`
- `cat id_rsa`
- paste private key into nano
- chmod 700 newuser.private
- changing owner from root to newuser: `sudo chown newuser:newuser authorized_keys`

## INSTALL APACHE

- Yum Updates:
`sudo yum update –y`

- After the updates complete, install the Apache web server with the PHP software package using the yum install command, which installs multiple software packages and related dependencies at the same time:


`sudo yum install -y httpd24 php56 php56-mysqlnd`
                
- Start the web server with the command shown following:

`sudo service httpd start`
`sudo systemctl start httpd`

https://www.liquidweb.com/kb/how-to-install-apache-on-centos-7/

#Step 2: Allow Apache Through the Firewall
-  Allow the default HTTP and HTTPS port, ports 80 and 443, through firewalld:

`sudo firewall-cmd --permanent --add-port=80/tcp`

`sudo firewall-cmd --permanent --add-port=443/tcp`

- And reload the firewall:

`sudo firewall-cmd --reload`

# Step 3: Configure Apache to Start on Boot
- And then start Apache:

`sudo systemctl start httpd`

- Be sure that Apache starts at boot:

`sudo systemctl enable httpd`

- To check the status of Apache:

`sudo systemctl status httpd`

- To stop Apache:

`sudo systemctl stop httpd`