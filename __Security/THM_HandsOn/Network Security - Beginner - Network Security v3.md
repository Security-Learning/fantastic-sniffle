Network Security - Beginner - Network Security v3
========================

## Beginner - Network Security v3

Introduction to Cyber Security -> Introduction to Offensive Security -> Network Security

### Step 1 - Recon

Gather Information
Target IP - a.b.c.d

`export $IP=<IP>`

 - `nmap $IP`

### Step 2 - Download data
we can see FTP (file transfer Protocol) port is open - try anonymous login
download the file using get command `get <fileName>`

### Step 3 - Attack
note the password, try login as root via ssh as ssh port is open
