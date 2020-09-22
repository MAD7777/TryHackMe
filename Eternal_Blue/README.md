# Eternal Blue 
#### About: 
  This machine known as BLue(Windows 7) based on vulnerablity known as Eternal Blue. The Wanna Cry worm which was a major randsome_ware attack exploited this vulnerability to spread itself across the network.
#### Links: 
* The room is hosted free on Tryhackme.com. Recommended for beginners.
* Link - https://tryhackme.com/room/blue

### Lests start with the Methodology.

#### Step 1: Information Gathering.
1. First of all we need to get connected to tryhackme's network using openvpn. Once connected Deploy the machine. *
If you don't know about the openvpn you can join this room https://tryhackme.com/room/openvpn

2. We will be using a tool called **Nmap** (network mapper) to gather information about the various service runnig on the machine.
Nmap is a great network scanning tool. https://tryhackme.com/room/rpnmap This room will help you with the basic of Nmap commannds.  

*Enough with the talk Let's get into scannig the machine.*
 
* Once the machine is deployed they will give an ip address. As shown in the Figure.
  ![ip](https://github.com/MaheshDuvaka/TryHackMe/blob/master/Eternal_Blue/images/ip.PNG)

* Now we will scan the ip to discover the open ports and the services running. we'll also use various option to discover vulnerabilities.
    ![nmap](https://github.com/MaheshDuvaka/TryHackMe/blob/master/Eternal_Blue/images/nmap.PNG)
  * **-sV** this option is used to determine service version.
  * **-O** this option is used to detect the OS of the machine.
  * **--script** this option helps in finging vulnerabilities using nmap scripiting engine.
* As we can see the scan gave an interesting result.
 ![scan](https://github.com/MaheshDuvaka/TryHackMe/blob/master/Eternal_Blue/images/scan.png)

The result states that the Microsoft SMBv1 server has a critical vunerability(**ms17-010**).
This vulnerability is known as Enternal Blue you can find the exploit on exploit-db as **CVE-2017-0143**.

#### Step 2: Gaining Access.

* This is probably the exciting part of every Hacker.
* we will be using **metasploit** to exploit the machine. It is a framework developed by **Rapid7**.
* https://tryhackme.com/room/rpmetasploit This room will help you to get familiar with Metasploit.
* Lets Fire up Metasploit by using command **msfconsole**
* As we see that Nmap is indicating the target may be vulnerable to ms17-010. Hence will do a simple search or *ms17-010*.
![ms.search](https://github.com/MaheshDuvaka/TryHackMe/blob/master/Eternal_Blue/images/ms.search.png)

* Now we know exploit to be used.

  ![use](https://github.com/MaheshDuvaka/TryHackMe/blob/master/Eternal_Blue/images/use.exploit.PNG)
* Before we run the exploit will just take a look at the option. 
 ![options](https://github.com/MaheshDuvaka/TryHackMe/blob/master/Eternal_Blue/images/options.PNG)

* This module has four required settings and three of them are automatically configured for you. The only thing you have to do is provide a target so we use the command:
  * set *rhost* [ip address of the machine] 
  * Then execute the exploit by **exploit** command
  * ![exploit](https://github.com/MaheshDuvaka/TryHackMe/blob/master/Eternal_Blue/images/exploit.PNG)
  * As we see the exploit worked and we got reserse shell back. Now we need to upgrade our shell to **Meterpreter** which is way powerfull..!!
#### Step 3: Escalate
  * The challenge wants us to convert our “regular” shell access on the target to a “meterpreter” shell, there is a module for that, all we need to do is load it.
  * First we will background the current shell by CRLT+Z, *Take note the session id*
  * Next search for the **shell_to_meterpreter**
  * ![escalate](https://github.com/MaheshDuvaka/TryHackMe/blob/master/Eternal_Blue/images/escalate.PNG)
