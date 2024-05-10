
# Metasploit-for-reconnaissance
## Metasploit
Metasploit for reconnaissance in pentesting

## AIM:

To get introduced to Metasploit Framework and to  perform reconnaissance  in pentesting .

## DESIGN STEPS:

### Step 1:

Install kali linux either in partition or virtual box or in live mode

### Step 2:

Investigate on the various categories of tools as follows:

### Step 3:

Open terminal and try execute some kali linux commands

### EXECUTION STEPS AND ITS OUTPUT:
Find out the ip address of the attackers system
#### OUTPUT:
![image](https://github.com/danush564/Metasploit-for-reconnaissance/assets/98585166/b6240723-ccef-44d8-b31c-35bccfd1db71)

Invoke msfconsole:

![image](https://github.com/danush564/Metasploit-for-reconnaissance/assets/98585166/783b3cae-a22c-4e22-b162-174ea086c0a5)

Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

![image](https://github.com/danush564/Metasploit-for-reconnaissance/assets/98585166/17a59133-ba75-43f9-9a78-58632f7b0bf8)

#### Port Scanning:
Following command is executed for scanning the systems on our local area network with a TCP scan (-sT) looking for open ports between 1 and 1000 (-p1-1000).
msf >  nmap -sT 192.168.1810/24 -p1-1000
#### OUTPUT:
![image](https://github.com/danush564/Metasploit-for-reconnaissance/assets/98585166/0e0fd9c5-6462-4e94-93d8-de5253b4c30b)
step4:
use the db-nmap command to scan and save the results into Metasploit's postgresql attached database. In that way, you can use those results in the exploitation stage later.

scan the targets with the command db_nmap as follows.
msf > db_nmap 192.168.181.0/24
#### OUTPUT:

![image](https://github.com/danush564/Metasploit-for-reconnaissance/assets/98585166/02ca6949-d9f2-4b3d-a70e-79204ead470b)

Metasploit has a multitude of scanning modules built in. If we open another terminal, we can navigate to Metasploit's auxiliary modules and list all the scanner modules.
cd /usr/share /metasploit-framework/modules/auxiliary
kali > ls -l
#### OUTPUT:

![image](https://github.com/danush564/Metasploit-for-reconnaissance/assets/98585166/c5cf3d67-b23f-477f-89ae-ddb08f56c363)

Search is a powerful command in Metasploit that you can use to find what you want to locate. 
msf >search name:Microsoft type:exploit

The info command provides information regarding a module or platform,
#### OUTPUT
![image](https://github.com/danush564/Metasploit-for-reconnaissance/assets/98585166/0d5eef1c-c0c8-4d9b-ae95-151140d5874e)

Before beginning, set up the Metasploit database by starting the PostgreSQL server and initialize msfconsole database as follows:
systemctl start postgresql
msfdb init
#### MYSQL ENUMERATION
Find the IP address of the Metasploitable machine first. Then, use the db_nmap command in msfconsole with Nmap flags to scan the MySQL database at 3306 port.
db_nmap -sV -sC -p 3306 <metasploitable_ip_address>

![image](https://github.com/danush564/Metasploit-for-reconnaissance/assets/98585166/411f00fe-9696-482e-b869-09992676d400)

Use the search option to look for an auxiliary module to scan and enumerate the MySQL database.
search type:auxiliary mysql

![image](https://github.com/danush564/Metasploit-for-reconnaissance/assets/98585166/d9073c11-781d-4fcc-a973-7140d78bcc0f)

use the auxiliary/scanner/mysql/mysql_version module by typing the module name or associated number to scan MySQL version details.
use 11 Or: use auxiliary/scanner/mysql/mysql_version

![image](https://github.com/danush564/Metasploit-for-reconnaissance/assets/98585166/a3420fe4-32c6-47bf-b739-ef9a1ef09a5a)


Use the set rhosts command to set the parameter and run the module, as follows:

![image](https://github.com/danush564/Metasploit-for-reconnaissance/assets/98585166/1f58b2c3-1767-400a-b060-de62cc701cbb)


After scanning, you can also brute force MySQL root account via Metasploit's auxiliary(scanner/mysql/mysql_login) module.

![image](https://github.com/danush564/Metasploit-for-reconnaissance/assets/98585166/8f7ed0ab-76c6-46bc-8161-bd1e28ac9f55)

set the PASS_FILE parameter to the wordlist path available inside /usr/share/wordlists:
set PASS_FILE /usr/share/wordlistss/rockyou.txt
Then, specify the IP address of the target machine with the RHOSTS command.
set RHOSTS <metasploitable-ip-address>
Set BLANK_PASSWORDS to true in case there is no password set for the root account.
set BLANK_PASSWORDS true

![image](https://github.com/danush564/Metasploit-for-reconnaissance/assets/98585166/d8e16d02-8040-4a51-b4bb-f25aa7e5da31)

#### RESULT:
The Metasploit framework for reconnaissance is  examined successfully.
