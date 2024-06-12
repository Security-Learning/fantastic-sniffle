OS Security - Beginner - OS Security v1
========================


## Beginner - OS Security v1

Hands on on Practical Examples of OS Security

Introduction to Cyber Security -> Introduction of Offensive Security -> Operating System Security


System admin account is called `root` in Android, Apple, Linux systems. While on MS Windows systems this account is called `administrator` These accounts have complete unrestricted access to a system

Connect via openVPN or open attackBox via web

check the mentioned username/passwords are valid or not via ssh login

`ssh <username>@<ip>`

when asked for password enter password

when you are typing the SSH password, you won't see stars, dots, or any indicator on the screen that the password is being typed. However, the system still receives the password you are entering.


Then check the other user login creds based on top most common passwords

check history to find the root creds

after root login -> find where the flag.txt file is located -> 
`find ~ -type f -name flag.txt` -> shows the location
`cat <loation>`