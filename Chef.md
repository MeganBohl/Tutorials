# 1-8 Configuring Your Development Environment - Microsoft Azure
# this command list is provided to accompany the demos in the Chef Fundamentals Udemy course

# run these commands to ensure you're setup properly.
# Commands are demonstrated on a MacOS terminal. If on a Windows machine, commands
# for navigation and file manipulation may vary.
# If unable to locate any of the tools, please ensure that your system path is 
# properly configured as documented in the setup pdf.

# all commands assume working out of the home directory, ~/

# follow the commands below to connect with the Azure instance with an ssh client
cd ~
ssh-keygen -t rsa -b 2048 -f ~/.ssh/azure
cat ~/.ssh/azure.pub

# After locating username and public ipaddress in the cloud console
ssh -i 	~/.ssh/azure username@PUBLIC_IP


# Run these commands on the cloud instance after connecting with ssh
username@centos7$ curl https://omnitruck.chef.io/install.sh | sudo bash -s -- -P chefdk -c stable -v 0.18.30
username@centos7$ chef --version
username@centos7$ sudo yum install nano -y
username@centos7$ sudo yum install vim -y
username@centos7$ exit

- First Recipe:  
```file '/hello.txt' do
  content 'Hello, world!'
end
```

`\`
`sudo chef-client --local-mode hello.rb`
`cat /hello.txt`
- make a change to show how client will repair it:
    - `sudo nano /hello.txt` 
    - enter random text & save
    - run chef client again `/`
        `sudo chef-client --local-mode hello.rb`
    - output should show corrected back to original recipe


# ~/setup.rb
```
package 'tree' do
	action :install
end

package 'ntp'

file '/etc/motd' do
	content 'This server is the property of ...'
	action :create
	owner 'root'
	group 'root'
end

```
-- 
# LEARN CHEF RALLY
## Configure a resource 

You ran a few basic Chef commands and got a flavor of what Chef can do. You learned that a resource describes one part of the system and its desired state. You worked with a file, which is one kind of resource.

* Resources describe the what, not the how
A recipe is a file that holds one or more resources. Each resource declares what state a part of the system should be in, but not how to get there. Chef handles these complexities for you.

In this module, you declared that the file /tmp/motd must exist and what its contents are, but you didn't specify how to create or write to the file. This layer of abstraction can not only make you more productive, but it can also make your work more portable across platforms.

Resources have actions
When you deleted the file, you saw the :delete action.

Think of an action as the process that achieves the desired configuration state. Every resource in Chef has a default action, and it's often the most common affirmative one – for example, create a file, install a package, and start a service.

When we created the file we didn't specify the :create action because :create is the default. But of course you can specify it if you want.

The documentation for each resource type, file for example, explains the type's default action.

Recipes organize resources
In Chef, hello.rb is an example of a recipe, or an ordered series of configuration states. A recipe typically contains related states, such as everything needed to configure a web server, database server, or a load balancer.

Our recipe states everything we need to manage the MOTD file. You used chef-client in local mode to apply that recipe from the command line.

* Chef Automate DNS Label:
- southcentralus

