# Linux

1. What is the Use of `echo` Command ?

echo is a command that outputs the strings that are passed to it as arguments.
```
echo "Hello World"
```
2. How to check the computer name or Hostname in Linux ?

Using `hostname` command
```
hostname
```

3. How to check the current user in Linux terminal ?
```
whoami
```
4. How to check your current path/diretory you are working in ?
```
pwd
```
5. Explain is diff b/w relative and absolute path ?

Relative path : Start from current working directory 
Absolute path : The full path to a file or directory.

6. Which command to be used to create a file in Linux ?

```
touch 
vi 
vim 
nano
cat > filename
```
7. How will you edit an existing file on Linux server 

Using `vi, vim, nano`

```
vi filename
```
8. How to Rename a file in Linux?

```
mv oldName newName
```
9. How to search for a string in a file ?

Grep - It will search for a word inside a file.

```
grep <wordName> <fileName>
```
(Or)

We can use `less`

```
less fileName 
```
You will enter into a file and type `/wordName` you will get it.

10. Diff b/w Grep and Egrep ?

In egrep, you can search for more than one string at same time
```
egrep "key1 | key2 | key3" <fileName>
```

11. How can you read a file without using cat command ?

using less, more, vi and nano 
```
less filename 
more filename
```

12. What is the advantage of using less command?

We can easily read big files.

Forward and Backword search is easy.

Navigation from top to bottom is easy.

13.


# File Permission 

31. What are the diff types of permissions for a file in Linux ?

Read (r)
Write (w)
Executable(x)

32. How to check permission given to a file ?
```
ls -l 
ll 
getfacl fileName
```
33. Which permission allow user to run an executable file(script)

```
executable (x)
```
## Redirection 

34. How to write the output of a command into a file ?

```
command > filename

Ex : ls -l > myfile.txt
ls -ltr
cat myfile.txt

we can share this file with anyone easily.
```
35. How to write something in a file without deleting the existing content?

We can append the file using `>>`
```
cat >> fileName
```
36. How to redirect an error of a command into a file ?

To redirect an error we need to use `2>`

To redirect both error and output `2>&1`

## Automation

37. How to automate any task or script ?

Using `Cron Jobs` 

For which we hae crontab and at command.

38. How to check scheduled jobs ?

```
crontab -l  # To check scheduled job list
```
39. What is the meaning of this cron job ? * * * * *

```
* minutes (0-59)

* hour (0-23)

* day of the month (1-31)

* month (1-12)

* day of thw week (0-6)
```

40. If your cron job didn't work, how would you check?

```
check system time

crontab entry 

check /var/log/messages
```

## Services

41. What is daemon service ?

Service that keep running in background.

ex: httpd, sshd, chronyd

42. How to check if a service is running or not ?

```
systemctl status <serviceName>
```

43. How to start/stop any service ?

```
systemctl start service
systemctl stop service
```

## System Monitoring 

44. How to check for free disk space ?

Using `df` command
```
df -h
```
45. How to check size of a directory content?

Using `du` command
```
du -h <folderName>
```

46. How to check CPU usage of a process ?

```
top 
```
## Process

47. What is a process in Linux 

An instance of a running program.

whenever you start a program/application or execute a command, a process is created.

For every process a unique no. is assigned which is called PID(Process ID)

48. How to check if process/application is running or not ?

```
ps -ef | grep httpd
```
49. How to terminate/stop running a process ?

```
kill 
```
50. Diff b/w kill and Kill -9

kill -9 will terminate a program forcefully.


## Networking 

51. How to check if a ip/server is accessible or not ?

using `ping` or `telnet` command

52. Which command to use to get info about ports ?

```
netstat -tl
```
53. How to check open port on linux system ?

```
netstat putan | grep <port_no>
netstat putan | grep <port_no>
```
54. How to check network interfaces in Linux ?

```
ifconfig
netstat 
```

55. Diff b/w Telnet and SSH

SSH is secured and Telnet is Not.

## SSH

56. Which service should be running on server to allow you to connect remotely.

```
ssh or sshd
```

57. What is SSH ?

SSH is a Secure shell is a network communication protocol that enables two computer/devices to communicate and share data.

58. Why it is as Secure shell.

Because communication b/w host and client will be in Encrypted format.

59. What is default port for SSH.

```
ssh - 22
http - 80 
https -443
```

60. Which command is used to access a linux system from a terminal or another linux server.

```
ssh user@198.67.x.x
```
## Archive 

61. If you want to transfer a larger file (10gb) remotely, what would be the first thing you will do ?

- First, compress the file using `tar, gzip, gunzip`

62. Difference b/w tar, gzip and gunzip ?







