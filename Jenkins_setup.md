- cd ets/sysconfig/network-scripts
- nano ifcg-en... (whatever the name of my config file is)

# SSH into Virtual Box
- open Settings->Network for the VM
- Click the little blue arrow next to the Advanced box
- Click the box at the bottom labelled "Port Forwarding"
- Click the green "+" to add a rule
- Add the rule Host IP="127.0.0.1", Host Port="2222", Guest IP="10.0.2.15", Guest Port="22"
- From the host (my Mac terminal), you should be able to "ssh -p2222 127.0.0.1"


#### SHARED FOLDERS 
Guest Additions:
#add your user to the vboxsf group

[meganbohl@localhost ~]$ `sudo usermod -aG vboxsf $(whoami)`
