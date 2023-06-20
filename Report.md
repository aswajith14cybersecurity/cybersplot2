# cybersploit 2 report
### aswajithj14@gmail.com
### aswajith14cybersecurity/cybersplot2
![vulnhun](https://github.com/aswajith14cybersecurity/cybersplot2/assets/104053455/471f7e8c-75a4-462e-ae00-aac5f24eb0c6)
## 1. Introduction 
This report is to provide a detail analysis and walkthrough of Cybersploit 2 Vulnhub CTF Challenge. This CTF is designed to test skills in various aspects of cybersecurity, including penetration testing, vulnerability assessment, and exploit development. This report will provide step by step guide to complete the challenge.
## 2. Objective
The objective of the Cybersploit 2 Vulnhub is to gain root access to vulnerable virtual machine by identifying and exploiting multiple security.
## 3. Methodology
This CTF challenges can be approached using the following methodology:
1.	Reconnanaissance: Gathering information about the target machine.
2.	Scanning and Enummeration: Scaninng the target machines for open port, services, and vulnerabilty.
3.	Vulnerability Assessment: Identify and analyze vulnerabilties in the target machine by analyzing the result of the scanning and enumeration phase.
4.	Exploitation: Exploiting the discovered vulnerabilties to gain access to target machine.
5.	Post-Exploitation: Onces access is gained, escalater privileges, maintain persistence,and locate flags or hidden information within the system.
3. Initial Reconnaissance:
⦁	Perform a network scan to identify the IP address of the target machine.
#### Command: netdiscover
![netdiscover](https://github.com/aswajith14cybersecurity/cybersplot2/assets/104053455/e7283be1-fea7-4f7d-a1c3-15c1baa7b949)
shows IP address of connected devices to the router.
## 4. Scanning and Enumeration: 
⦁	Using Nmap to scan the open ports and vulnerabilties of the target machines.
#### Command: nmap -A 192.168.1.3 -vv
![Nmap scan1](https://github.com/aswajith14cybersecurity/cybersplot2/assets/104053455/d629683e-7202-4351-b4c5-4cc88fab5164)
![Nmap scan2](https://github.com/aswajith14cybersecurity/cybersplot2/assets/104053455/fe8f3a90-e44a-4cac-be38-ed32c1f2079d)
Here we got two open ports from the nmap result (Port 22 SSH and port 80 HTTP) So lets explore these vulnerabilties on target machine.
## 5. Vulnerability Assessment:
To enumerate the target machine with the HTTP port, open a web browser and enter the target machine's IP address to access the webpage.
#### Webpage:
![webpage1](https://github.com/aswajith14cybersecurity/cybersplot2/assets/104053455/67455079-d77c-4c50-968e-6a8ce38109fc)
Here we got a list of usernames and password, But in this list we can found a string so lets check the source code for more infomation which may help us.
![source code](https://github.com/aswajith14cybersecurity/cybersplot2/assets/104053455/48a81bbc-273d-4d2b-87a2-4a0e073f67d1)
![source code2](https://github.com/aswajith14cybersecurity/cybersplot2/assets/104053455/5fc529fb-3ef1-456c-b564-07ef09b2bfa7)
After going through the source code of the home page showed a comment indicating <!----------ROT47---------->
ROT47 : ROT47 is a simple character substitution cipher that rotates each letter by 47 positions in the ASCII table, effectively encoding and decoding text.
Now, let's copy the string (4 point from the table) from the webpage and attempt to decode it.
![decrypt](https://github.com/aswajith14cybersecurity/cybersplot2/assets/104053455/055f49b5-9bbf-4bc8-a4e3-54206980e293)

#### decode result: shailendra cybersploit1
## 6. Exploitation:
Here we have two clear text credentials. so lets use them to login into target machine. As we know that port 22 is open (from the nmap result) so lets try to login through ssh.
![ssh login](https://github.com/aswajith14cybersecurity/cybersplot2/assets/104053455/ee8bb9a2-e4a2-47ce-828a-a30bf2ed8018)

After login, Ran a few commands to gather information about the os (operating system). After going through some of the command we got a txt file which is named as hint.txt and we the file is opened it shows a text "docker" . This means the docker is being used in the target machine.
Commands: 1. ls (list the file)
                   2. cat hint.txt (to read the txt file)
                   3. id ( is used to find out user and group names and numeric ID's (UID or group ID)               of the current user) 
#### Docker privilege escalation:
To do the privilege escalation vulnerability to get the root access, Here i used Gtfobins (https://gtfobins.github.io/)
![docker prv](https://github.com/aswajith14cybersecurity/cybersplot2/assets/104053455/e9cd0265-0524-4b1c-8714-20c21529657e)
![privileg1 1](https://github.com/aswajith14cybersecurity/cybersplot2/assets/104053455/a418b22c-8954-4727-bf1e-9567660ee4a2)
Now the payload successfully worked and we got root access. Now lets search for final flag in root directory.

![final flag](https://github.com/aswajith14cybersecurity/cybersplot2/assets/104053455/e1ce281b-5c49-47c1-b42d-4e43dce2cbb7)

#### We got the final flag.......








