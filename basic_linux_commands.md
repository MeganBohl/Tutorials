## Add a Second User
- Add a second user and set the password 
- `adduser megan passwd username`
- write down the username and password done
- login and backout to test the username
    - give user root privileges: `gpasswd -a megan wheel`
- require user to change password at login:  `chage -d 0 {user-name}`
                                            (chage is not a misspelling, 0 is the amount of time required to reset pwd, 0 minutes)
-  add sudo user: `sudo gpasswd -a username wheel`
-  remove sudo user: `sudo gpasswd -d username wheel`
-  `sudo -s`, you will get the root terminal

-  Pipe `|` passes output to program a utility 
-  Redirect `>` passes output to file or stream
-  Tee `ls -1 *.txt | wc -l | tee count.txt`
## Redirects stderr (fd 2) to the black hole (discard output of the command).

-  The > operator redirects the output usually to a file but it can be to a device. You can also use >> to append.

 If you don't specify a number then the standard output stream is assumed but you can also redirect errors

> file redirects stdout to file
1> file redirects stdout to file
2> file redirects stderr to file
&> file redirects stdout and stderr to file

/dev/null is the null device it takes any input you want and throws it away. It can be used to suppress any output.

# Change both owner and the group

# ls -l tmpfile
-rw-r--r-- 1 root family 0 2012-05-22 20:03 tmpfile

# chown himanshu:friends tmpfile


## File Permission Examples: 
Permissions:
1 – can execute
2 – can write
4 – can read

The octal number is the sum of those free permissions, i.e.
3 (1+2) – can execute and write
6 (2+4) – can write and read

Position of the digit in value:
1 – what owner can
2 – what users in the file group(class) can
3 – what users not in the file group(class) can

##Examples:
chmod 600 file – owner can read and write
chmod 700 file – owner can read, write and execute
chmod 666 file – all can read and write
chmod 777 file – all can read, write and execute

#Save permanently to PATH
- `nano ~/.bash_profile`
- `export PATH="~/opt/maven/bin:$PATH"`   (where /opt/maven/bin is - interchangeable for file you want to add)
- In new terminal:
`echo $PATH`