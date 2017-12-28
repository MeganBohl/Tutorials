##### GUEST ADDITIONS
https://www.if-not-true-then-false.com/2010/install-virtualbox-guest-additions-on-fedora-centos-red-hat-rhel/
`yum update kernel*`
`reboot`
`mkdir /media/VirtualBoxGuestAdditions`
`mount -r /dev/cdrom /media/VirtualBoxGuestAdditions`
`rpm -Uvh https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm`
`yum install gcc kernel-devel kernel-headers dkms make bzip2 perl`
`KERN_DIR=/usr/src/kernels/`uname -r`
`export KERN_DIR`

#INSTALL GNOME GUI
https://www.cyberciti.biz/faq/howto-install-gnome-gui-desktop-on-centos-rhel-7-server/
- To see what yum pkg are avail: 
`yum grouplist`
`yum group install "GNOME Desktop" "Graphical Administration Tool`
`sudo yum groups install "Server with GUI"`
`sudo systemctl set-default graphical.target`

- Follow steps, stop before installing CD, didn't work
- Go to Finder>VirtualBox>MacOs>VirtualBoxGuestadditions.iso
- copy to desktop
- go to CentOs minimal box and click on small CD in lower right-hand and install manually from desktop

- In Virtual Box Guest machine, Devices>Shared Clipboard AND Devices, chance to BIDIRECTIO
NAL.  Then you should be able to copy and paste to and from host & guest machines.


## SSH into VirtualBox

* Need to be able to connect from the host machine into the guest OS where the guest is inside virtualbox
- Open Settings->Network for the VM
- Click the little blue arrow next to the Advanced box
- lick the box at the bottom labeled "Port Forwarding"
- Click the green "+" to add a rule
- Add the rule Host IP="127.0.0.1", Host Port="2222", Guest IP="10.0.2.15", Guest Port="22"
- From the host, you should be able to "ssh -p2222 root@127.0.0.1"


##INSTALL JENKINS
https://www.vultr.com/docs/how-to-install-jenkins-on-centos-7
cat /var/lib/jenkins/secrets/initialAdmin/Password


## Shared Folder setup:
https://www.techrepublic.com/article/how-to-share-folders-between-guest-and-host-in-virtualbox/

* add your user to the vboxsf group using this command:`
- In VBox>Devices>Shared Folders, click + button to add new shared folder
    * connect it to your host file:  /Users/Guest/Public
    * Click to enable Auto-mount

Mount the shared folder from within the guest:
- In terminal
- Mount the shared folder:  `sudo mount -t vboxsf Public ~/Public`
- Open your file manager, and you should see the contents of ~/Public (from the host) in the folder ~/Public (on the guest).

#Used to increase size in VB-Didn't get it to work:
https://stackoverflow.com/questions/1688690/how-can-i-easily-add-storage-to-a-virtualbox-machine-with-xp-installed
- In terminal:
`VBoxManage modifyhd CentosMinimalJenkins12-6-17Clone.vdi --resize 23040`
 `VBoxManage modifyhd /Users/meganbohl/VirtualBox   VMs/CentosMinimalJenkins12-6-17Clone/CentosMinimalJenkins12-6-17Clone.vdi --resize 23040`
- use a binary number to resize VM HD to
`VBoxManage modifyhd --resize 23040 /Users/meganbohl/VirtualBox VMs/CentosMinimalJenkins12-6-17Clone/CentosMinimalJenkins12-6-17Clone.vdi`

`VBoxManage clonehd file.vdi output.img --format RAW`


