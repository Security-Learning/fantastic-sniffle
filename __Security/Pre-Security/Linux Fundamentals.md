Linux Fundamentals
========================


`echo` -> output any text we provide
    <code>echo "HI MOM"</code>

`whoami` -> find out what user we are currently logged in as


## Interacting with File System

| Command | Description |
| - | - |
| ls | listing files/folders in the current working directory |
| cd | change working directory |
| cat | concatenate |
| pwd | print working directory |


## Searching for Files
<code>find</code> command is fantastic in sense that it can be sued both very simply or rather complex depending upon what is you want to do exactly. 

<code>find -name pass.txt</code> -> this will search for the file name pass.txt within the current working directory

we can use regex to find files following a specific pattern.


The <code>grep</code> command allows us to search the contents of files for specific values that we are looking for.

We can use "grep" to search entire contents of file or piped output data for any entries of the value that we are searching for.


## Shell Operators

1. & -> Allows you to run commands in the background of your terminal
2. && -> Allows you to combine multiple commands together in one line of your terminal
3. > -> is a redirector => meaning that we can take the output from a command and direct it elsewhere
4. >> -> does the same function as ">", but appends the output rather than replacing


## SSH into linux machine

SSH simply is a protocol between devices in an encrypted form. Using cryptography, any input we send in a human readable format is encrypted for travelling over a network where it is then unencrypted once it reaches the remote machine

SSH allows us to remotely execute commands on another device remotely

Any data sent between the devices is encrypted when it is send over a network such as the internet

```bash
ssh <username>@<IP>
```


## Introduction to switches and flags
A majority of commands allow for arguments to be provided. These arguments are identified by a hypen and a certain keyword known as flags or switches

Commands that accept "--help" option, will list the possible options that the command accepts, provide a brief description and example of how to use it.

the manual pages are a great source of information for both system commands and applications available on both a linux machine, which is accessible on the machine itself and online

To access the documentation of a command, we can use the <code>man</code> command and then provide the command we want to read the documentation for.


## File System interaction

| command | description |
| - | - |
| touch | create new file |
| mkdir | create a folder |
| cp | copy a file or folder |
| mv | move a file or folder |
| rm | remove a file or folder |
| file | determine the type of a file |

`touch note.md` => will create a note.md file


## Permissions 101
A file or folder can have a couple of characteristics that determine both what actions are allowed and what user or group has the ability to perform the given action such as Read, Write, Execute

If the permissions have been set, then a group of users can also have either the same or a different set of permissions to the exact same file without affecting the file owner itself.

`su -l <user>` -> to switch between users in linux 


## Common Directories

`/etc` is common place to store system files that are used by your operating system
Linux stores passwords in a file encrypted using sha512 algorithm

`/var` is one of the main root folders found on a linux os. This folder stores data that is frequently accessed or written by services or applications running on the system. Example, log files from running services and applications are written in `/var/log` or other data that is not necessarily associated with specific user.

`/tmp`, unique root directory, is volatile and is used to store data that is only needed to be accessed once or twice. Similar to memory on your computer, once the computer is restarted, the contents of this folder are cleared out.



## Downloading files(wget)
`wget` allows us to download files from the web via HTTP

Ex: `wget https://coachbeard.vercel.com`


## Transferring files from your host - SCP
Secure copy (SCP) - means of securely copying files between 2 computers using the SSH protocol to provide both authentication and encryption.

SCP allows you to copy files from current system to remote system and vice-versa

`scp <source> <destination>`

`scp <localFile/Folder> <remoteUserName>@<remoteIP>:<remoteFileLocation>`

`scp <remoteUsername>@<remoteIP>:<remoteFileLocation> <localFile/Folder>`



## Serving Files from your host -WEB
Python helpfully provides a lightweight and easy to use module called "HTTPServer". This module turns your device into a quick and easy server that you can use to serve your own files, where they can then be downloaded by another computer using commands such as `curl` or `wget`

`python3 -m http.server` -> spins up webserver with default port 8000


## Processes 101
Processes are programs that are running on your machine. They are managed by the kernel, where each process will have an ID assocaited with it, also known as PID.

We can use <code>ps</code> command to provide a list of the running processes as our users session and some additional information such as status code, the session that is running it and its CPU usage and the name of the actual program or command being executed.

To see the processes run by other users and those that dont run from a session, we need to provide **aux** to ps command like <code> ps aux</code>

<code>top</code> command gives you real-time statistics about the processes running on your system instead of a one-time view. These statistics will refresh every 10 seconds, but will also refresh when you use arrow keys to browse various rows.


You can send signals that terminate processes. To kill a command , we can use the appropriately named <code>kill</code> command and the associated PID that we wish to kill.

Some of the signals that we can send to a process when it is killed:
1. SIGTERM - kill the process, but allow it to do some cleanup tasks beforehand
2. SIGKILL - Kill the process, doesnt do any cleanup after the fact
3. SIGSTOP -> Stop/suspend the process.


### How do processes start?
The OS uses namespaces to ultimately split up the resources available on the computer to processes. 

Namespaces are great for security as it is a way of isolating process from another -- only those that are in the same namespace will be able to see each other

The process with an ID of 0 is a process that is started when the system boots. This process is the systems init on ubuntu such as **systemd**, which is used to provide a way of managing a users processes and sits in between the os and the user.

Any program or piece of software that we want to start will start as whats known as a child process of *systemd*. This means that it is controlled by systemd, but will run as its own process(although sharing the resources from systemd) to make it easier for us to identify

Some applications can be started on the boot of the system that we own. This can be done using ,code>systemctl [option] [service]</code> command, this command allows us to interact with the systemd process.


We can do 4 options with `systemctl`
1. start
2. stop
3. enable
4. disable


### Backgrounding and Foregrounding in Linux

Processes can run in two states. In the background and in the foreground.

After adding "&" to the command at the end, we are given and ID of the process and process starts its job in the background.

We can do the exact same when executing things like scripts -- rather than relying on the & operator, we can use `ctrl - z` on keyboard to background a process.

With our process backgrounded, we can use `fg` to bring this back to focus


## Maintaining Your System: Automation

Crontab is one of the process that is started during boot, which is responsible for facilitating and managing cron jobs.

A crontab is simply a special file with formatting that is recognised by the `cron` process to execute each line step-by-step. crontabs require 6 specific values:
1. MIN - what minute to execute at
2. HOUR - what hour to execute at
3. DOM - what day of month to execute at
4. MON - what month of year to execute at
5. DOW - what day of week to execute at
6. CMD - the actual command that will be executed


An interesting feature of crontabs is that these also support the wildcard or asterisk (*). If we do not wish to provide a value for that specific field, i.e. we don't care what month, day, or year it is executed -- only that it is executed every 12 hours, we simply just place an asterisk.



## Package Management
When developers wish to submit software to the community, they will submit it to an "apt" repository. If approved their programs and tools will be released to the world to use.

We can use apt command to install software onto our ubuntu system. The `apt` command is a part of the package management software also named apt. This contains a whole suite of tools that allows us to manage the packages and sources of our software, and to install or remove at the same time.

One method of adding repositories is to use the `add-apt-repository` command. 

When adding software, the integrity of what we download is guaranteed by the use of what is called GPG(Gnu Privacy Guard) keys. These keys are essentially a safe check from the developers saying " here's our software". If the keys do not match up to what your system trusts and what the developers used, then the software will not be downloaded.

To add a new third party software (example sublime text):
1. Download the GPG key and use apt-key to trust it
    - <code> wget -qO - https://download.sublimetext.com/sublimehq-pub.gpg | sudo apt-key add - </code>
2. We have added this GPG key to our trusted list, we can now add third party repository to our apt sources list. 
3. create new file in `/etc/apt/sources.list.d` directory
4. enter the repository information and save the software repository into newly created file in sources.list.d file ( ex: deb https://download.sublimetext.com apt/stable)
5. After we have added this entry, we need to update apt to recognise this new entry -- this is done using the `apt update` command.
6. Once successfully updated, we can not proceed to install the software that we have trusted and added to apt using  `apt install sublime-text`
7. Removing software is the reverse process till step 6, or `apt remove [software]`


## Logs
Log are located in `/var/log` directory, these files and folders contain logging information for applications and services running on your system