
* Dave found bots trying to get into his VM, in /var/log/secure
1.  cd /etc/ssh
2.  sudo cp sshd_config sshd_config.bak
3.  yum install nano
4.  sudo nano sshd.config
5.  add port (arbitrary # like 45678), all IPS 
    Port 45678

6.  restart SSH 
7.  Add port to servers security group in AWS  (TCP)
8.  Connect via my new port: `ssh -i "MeganAWS.pem" ec2-user@meganaws.mywire.org -p 22`

8.  To check if connected to correct port:
    `netstat -anp | grep 45678`

9. Removed connection to port 22 in sshd_config file by removing Port 22 line
/etc/ssh/sshd_config
    sudo nano sshd.config

ssh@meganaws.mywire.org


