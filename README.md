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

<img width="681" height="447" alt="image" src="https://github.com/user-attachments/assets/360c08c9-7182-40af-9735-4f5f225ff342" />
Invoke msfconsole:
## OUTPUT:

<img width="945" height="572" alt="image" src="https://github.com/user-attachments/assets/65e6e564-e394-4a8d-b171-2988623e1ce4" />

Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.




Port Scanning:
Following command is executed for scanning the systems on our local area network with a TCP scan (-sT) looking for open ports between 1 and 1000 (-p1-1000).
msf >  nmap -sT 10.210.109.149/24 -p1-1000  (Replace with appropriate IP Address)
## OUTPUT:

<img width="637" height="262" alt="image" src="https://github.com/user-attachments/assets/6d9bf698-7f9e-40e3-9172-e6c1bbf60318" />

step4:
use the db-nmap command to scan and save the results into Metasploit's postgresql attached database. In that way, you can use those results in the exploitation stage later.


scan the targets with the command db_nmap as follows.
msf > db_nmap 10.210.109.149/24
## OUTPUT:

<img width="1742" height="458" alt="image" src="https://github.com/user-attachments/assets/cb34ff92-16c6-4676-a6e7-cdfb53f2a54c" />


Metasploit has a multitude of scanning modules built in. If we open another terminal, we can navigate to Metasploit's auxiliary modules and list all the scanner modules.
cd /usr/share /metasploit-framework/modules/auxiliary
kali > ls -l
## OUTPUT:
<img width="946" height="722" alt="image" src="https://github.com/user-attachments/assets/e495ff2d-ac5a-4ceb-ab2b-95e5d86c4c28" />



Search is a powerful command in Metasploit that you can use to find what you want to locate. 
msf >search name:Microsoft type:exploit
## OUTPUT:

<img width="986" height="730" alt="image" src="https://github.com/user-attachments/assets/5595a4aa-4659-47a7-83fd-d11ed422bef8" />


The info command provides information regarding a module or platform,

Before beginning, set up the Metasploit database by starting the PostgreSQL server and initialize msfconsole database as follows:
systemctl start postgresql
msfdb init
## OUTPUT:

<img width="810" height="712" alt="image" src="https://github.com/user-attachments/assets/8bb4c858-a366-448f-b54a-7db951dbf328" />



## MYSQL ENUMERATION
Find the IP address of the Metasploitable machine first. Then, use the db_nmap command in msfconsole with Nmap flags to scan the MySQL database at 3306 port.
db_nmap -sV -sC -p 3306 10.210.109.149

## OUTPUT:

Use the search option to look for an auxiliary module to scan and enumerate the MySQL database.
search type:auxiliary mysql
## OUTPUT:
<img width="681" height="447" alt="image" src="https://github.com/user-attachments/assets/360c08c9-7182-40af-9735-4f5f225ff342" />

use the auxiliary/scanner/mysql/mysql_version module by typing the module name or associated number to scan MySQL version details.
use 11
Or:
use auxiliary/scanner/mysql/mysql_version
## OUTPUT:

<img width="806" height="312" alt="image" src="https://github.com/user-attachments/assets/34c7e248-9be1-4dd0-bf40-aad2d8c6edc5" />



Use the set rhosts command to set the parameter and run the module, as follows:
## OUTPUT:

<img width="808" height="182" alt="image" src="https://github.com/user-attachments/assets/d1bd44f7-b2dd-49a3-919d-e161a95453d2" />


After scanning, you can also brute force MySQL root account via Metasploit's auxiliary(scanner/mysql/mysql_login) module.
## OUTPUT:


<img width="805" height="561" alt="image" src="https://github.com/user-attachments/assets/bb489a51-8530-43bf-9e9c-fb8ab2fac9ee" />


set the PASS_FILE parameter to the wordlist path available inside /usr/share/wordlists:
set PASS_FILE /usr/share/wordlistss/rockyou.txt
Then, specify the IP address of the target machine with the RHOSTS command.
set RHOSTS <metasploitable-ip-address>
Set BLANK_PASSWORDS to true in case there is no password set for the root account.
set BLANK_PASSWORDS true
## OUTPUT:

<img width="807" height="578" alt="image" src="https://github.com/user-attachments/assets/0e6dcf2b-67cb-49fd-ad34-ca1df6e01b8e" />





## RESULT:
The Metasploit framework for reconnaissance is  examined successfully
