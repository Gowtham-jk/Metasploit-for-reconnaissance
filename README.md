# Metasploit-for-reconnaissance
# Metasploit
Metasploit for reconnaissance in pentesting

# AIM:

To get introduced to Metasploit Framework and to  perform reconnaissance  in pentesting .

## DESIGN STEPS:

### Step 1:

Install kali linux either in partition or virtual box or in live mode

### Step 2:

Investigate on the various categories of tools as follows:

### Step 3:

Open terminal and try execute some kali linux commands

## EXECUTION STEPS AND ITS OUTPUT:

Find out the ip address of the attackers system
## OUTPUT:
![1](https://github.com/user-attachments/assets/7e063c93-7584-48dd-8183-fba8761e9c3c)


Before beginning, set up the Metasploit database by starting the PostgreSQL server and initialize msfconsole database as follows:
> systemctl start postgresql

> msfdb init

Invoke msfconsole:
## OUTPUT:
![2](https://github.com/user-attachments/assets/0151f9f0-f1be-435e-bbd7-1c79fefa2b25)



Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.
![3](https://github.com/user-attachments/assets/7e96de0f-7729-4649-8cc3-02ba908102bc)



Port Scanning:
Following command is executed for scanning the systems on our local area network with a TCP scan (-sT) looking for open ports between 1 and 1000 (-p1-1000).
msf >  nmap -sT 192.168.1810/24 -p1-1000
## OUTPUT:
![4](https://github.com/user-attachments/assets/901a8fe9-689f-43bb-b385-1ac7e977a85c)


step4:
use the db-nmap command to scan and save the results into Metasploit's postgresql attached database. In that way, you can use those results in the exploitation stage later.

scan the targets with the command db_nmap as follows.
msf > db_nmap 192.168.181.0/24
## OUTPUT:

![5](https://github.com/user-attachments/assets/9470c7e2-1e1a-4400-b760-0182bc9c5ce0)


Metasploit has a multitude of scanning modules built in. If we open another terminal, we can navigate to Metasploit's auxiliary modules and list all the scanner modules.
cd /usr/share /metasploit-framework/modules/auxiliary
kali > ls -l
## OUTPUT:

![6](https://github.com/user-attachments/assets/cd9cbdf0-3587-4230-be7b-d0506b5beb38)


Search is a powerful command in Metasploit that you can use to find what you want to locate. 
msf >search name:Microsoft type:exploit
## OUTPUT

![7](https://github.com/user-attachments/assets/e3978894-43f3-4589-9573-550e97bfaee7)


The info command provides information regarding a module or platform,

![8](https://github.com/user-attachments/assets/3a210938-dba1-43ac-b812-73e0d0cd3390)


Before beginning, set up the Metasploit database by starting the PostgreSQL server and initialize msfconsole database as follows:
> systemctl start postgresql

> msfdb init

## MYSQL ENUMERATION
Find the IP address of the Metasploitable machine first. Then, use the db_nmap command in msfconsole with Nmap flags to scan the MySQL database at 3306 port.
db_nmap -sV -sC -p 3306 <metasploitable_ip_address>

![9](https://github.com/user-attachments/assets/108dfb4c-53a5-4684-abac-14c297182858)


Use the search option to look for an auxiliary module to scan and enumerate the MySQL database.
search type:auxiliary mysql
![10](https://github.com/user-attachments/assets/ae715d0b-3249-4b1e-ab00-bedfb54791cc)



use the auxiliary/scanner/mysql/mysql_version module by typing the module name or associated number to scan MySQL version details.
use 11
Or:
use auxiliary/scanner/mysql/mysql_version


![11](https://github.com/user-attachments/assets/aada0e2e-9f3f-45e0-98d7-05f155e56ca8)


Use the set rhosts command to set the parameter and run the module, as follows:

![12](https://github.com/user-attachments/assets/990d4bcb-b505-4548-bae1-0acd2703ecf8)


After scanning, you can also brute force MySQL root account via Metasploit's auxiliary(scanner/mysql/mysql_login) module.

![13](https://github.com/user-attachments/assets/ace12975-c6b7-4904-9ac8-88e08f97695b)


set the PASS_FILE parameter to the wordlist path available inside /usr/share/wordlists:
> set PASS_FILE /usr/share/wordlists/rockyou.txt
Then, specify the IP address of the target machine with the RHOSTS command.
> set RHOSTS <metasploitable-ip-address>

Set BLANK_PASSWORDS to true in case there is no password set for the root account.

>set BLANK_PASSWORDS true

![14](https://github.com/user-attachments/assets/d04bd454-3359-4113-bb47-8ed2969f2243)



## RESULT:
The Metasploit framework for reconnaissance is  examined successfully
