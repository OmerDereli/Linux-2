# Linux-2
Let's dive more in Linux commands

**Process Management**:
1-1-Launch a terminal and use the "ps" command to list all running processes.
```
$ ps -e #(all running process)
$ ps -u username #(user's all running process)
```

extra info: "top" for provides a dynamic real-time view of a running system.

1-2-Identify a process by its name or process ID (PID) that you want to terminate.
```
pidof "programname"
```
1-3-Use the "kill" command to gracefully terminate the selected process.
```   
kill -2 `pidof programname`
```
notes: 
kill -1 → Hangup (Closing window)
kill -2 → Interrupt (Control + C)
kill -9 → Kill
kill -15 → Terminate
 
1-4-Try terminating a process forcefully using the "kill -9" command.
```      
kill -9 `pidof programname`
```

--------------------------------------------------------------------------------------

--------------------------------------------------------------------------------------

**Working with Networking**:

2-1  Use the "ping" command to check the connectivity to a website (e.g., "ping www.example.com").
``` 
 $ ping google.com
```

2-2 Use the "ifconfig" or "ip addr" command to display information about your network interfaces.
```   
$ ifconfig
$ ip addr
```

2-3 Use the "curl" or "wget" command to download a file from the internet.
```
$ curl https://www.digitalocean.com/robots.txtcurl https://www.digitalocean.com/robots.txt
```   
notes:  
The main differences are:

wget's major strong side compared to curl is its ability to download recursively.
wget is command line only. There's no lib or anything, but curl's features are powered by libcurl.
curl supports FTP, FTPS, GOPHER, HTTP, HTTPS, SCP, SFTP, TFTP, TELNET, DICT, LDAP, LDAPS, FILE, POP3, IMAP, SMTP, RTMP and RTSP. wget supports HTTP, HTTPS and FTP.
curl builds and runs on more platforms than wget.
wget is released under a free software copyleft license (the GNU GPL). curl is released under a free software permissive license (a MIT derivate).
curl offers upload and sending capabilities. wget only offers plain HTTP POST support.
You can see more details at the following link:
   

2-4 Use the "netstat" command to view open network connections on your system.
```
$ netstat
```

--------------------------------------------------------------------------------------

--------------------------------------------------------------------------------------


**User and Group Management**:
    
3-1 - Create a new user account and assign it to a custom user group.

```
#first i need to create a group then i will ad users to it. for this:

$ sudo groupadd "groupname" to see groups compgen -g
#to add a user to group use
$ sudo usermod -a -G grouptest example
#to see what is inside group "getent group groupname"
```
        
3-2  Modify the user's home directory and shell using the "usermod" command.
```    
$ sudo usermod -d /new/home/directory deneme
# to see home folder "~username"
```
    
3-3 Create a file accessible only to the newly created user group.

```
$ sudo su
$ cd ..
$ exit
$ touch filename.txt
$ sudo chown :groupname filename.txt
$ sudo chmod 640 filename.txt
```
    
3-4  - Add and remove users from the group and observe how file access changes.
    
```	
$ sudo gpasswd -d deneme(username) grouptest(groupname)
```

--------------------------------------------------------------------------------------

-------------------------------------------------------------------------------------- 

**Working with System Logs**:
    
4-1  Examine system log files in the "/var/log" directory, such as "syslog" or "messages."

```
#to do that change the directory to var/log
$ cd /var/log
#to view logs use the "less" command. 
#The "dmesg" command prints the kernel ring buffer. By default, the command will display all messages from the kernel ring buffer.(note there are lots of lines so use dmesg | less )
#Note: SHIFT + G to scroll bottom.
```     
    
4-2 Use the "grep" command to search for specific keywords or events in the log files.
 
```   
$ grep 'Spotify' syslog
```
notes: 
"^" Denotes the beginning of a line
"$" Denotes the end of a line
"." Matches any single character
"*" The preceding item in the regular expression will be matched zero or more times
"[]" A bracket expression is a list of characters enclosed by [ and ]. It matches any single character in that list; if the first character of the list is the caret ^ then it matches any character not in the list
"\<" Denotes the beginning of a word
"\>" Denotes the end of a word    
       
4-3 Redirect log entries related to a specific process into a separate text file.

```    
$ grep 'spotify' /var/log/syslog > cat > mylogfile.txt 
```
     
4-4 Use the "tail" command to monitor real-time log entries as they are written to the file.

```
$ tail -f -n 5 /var/log/syslog
#"-f" to continue to see logs file
#"-n" for how many lines i want to see
```

--------------------------------------------------------------------------------------

-------------------------------------------------------------------------------------- 

**Basic Shell Scripting - Automation**:
5-1 Write a Bash script that automates a simple task, such as creating backups of a specific directory.
```    
#note:"env" or "which bash" to see location
```        
5-2 Include comments to explain the script's purpose and each step.
```    
#to use comments "#"
```   
5-3 Make the script executable and run it to verify its functionality.
```    
#to run script;
$ sh ./bashname.sh 
#and to make it executable #!bin/bash
```    
5-4 Schedule the script to run at a specific time using "cron" to automate the task regularly.
```    
#to use cron and edit;
$ crontab -e
```
```
#result 
#!bin/bash   #to make it executable 

backuptime=`date +%d-%b-%Y` #to give the folder name backup day
cp -R notlar backup #copy file
cd backup #to use mv easier changing locations to backup
mv notlar notlar_$backuptime # to change folder's name
```
              


  
