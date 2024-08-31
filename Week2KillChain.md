# Kill Chain & Debian 

# Table of Contents
-  [X)](#X)
-  [A)](#A)
-  [B)](#B)
-  [C)](#C)
-  [D)](#D)
-  [E)](#E)
-  [F)](#F)
-  [Sources](#Sources)

## X) Document Summary - Intelligence Driven Computer Network Defense
In this document, employees at Lockheed Martin's Cyber Security team analyse a major change in cybersecurity attack patterns and showcase
effective methods to counter it.

Previously, a majority of corporations relied on technologies and processess originally intended to mitigate the risk of legacy methods of cyber attacks such as
automated viruses & worms. However, a new class of threats called APT or Advanced Persistent Threat began to emerge, and previous methods of deterring cyber attacks were
no long viable against these APT-intrusions. The threat actors perpetrating these APT attacks would attempt intrusion after intrusion, adjusting their operations based on the success
or faliure of each attempt, meaning the previous common doctrine, which was the equivalent of putting up a digital wall, was not sufficient anymore if attackers could simply go around the wall.

These aforementioned threat actors would not be deterred by anti-virus software or quick patches, and they would often target end users directly with the ultimate goal of obtaining
sensitive intellectual property. One method of attack was using so-called "zero-day" exploits. These are previously unknown structural weaknesses in software that can not be effectively mitigated as their existence is unknown to the defending party. However, if analysts couldn't account for what they didn't know, they could prepare for what they knew: the attacker's next step.

This is where the Kill Chain Model comes in. Analysts devised an effective model of the necessary steps an attacker needs to make to gain access to a computer network.
Here's Lockheed Martin's Cyber Kill Chain:

 1. Reconnaisance - Harvesting email addresses, conference information etc.
 2. Weaponisation - Coupling exploit with backdoor into deliverable payload
 3. Delivery - Delivering weaponised bundle to the victim via email, web, USB, etc.
 4. Exploitation - Exploiting a vulnerability to execute code on a victim's system
 5. Installation - Installing malware on the asset
 6. Command & Control (AKA C2) - Command channel for remote manipulation of the victim
 7. Actions on Objectives - With 'Hands on Keyboard' access, intruders accomplish their original goals

Using this model, once an intrusion is detected, defenders can prevent further access into their system. In the document, LM provides an Action Matrix (Table 1) with appropriate methods of retaliation towards attackers for each kill chain step.
However, the aforementioned zero-day exploits still pose a big threat, and are by their nature hard to prepare for. LM has identified that if the attackers utilise zero-day exploits but reuse tools or methods from or in other phases of the kill chain, the benefits of utilising the exploit may be next to nothing if the attackers are still mitigated before or after the exploit's use, disarming the threat.

In fact these reuses of tools and methods are highlighted as an incredibly useful tool in neutralising APTs from the same threat actors. Analysing these intrusions allow defenders to identify these commonalities and overlapping indicators. Profiling threat actors in what are called 'Campaign Analyses' is yet another effective method provided toward's LM's suggestions of simultaenously reactive yet in a way, proactive defense.

Lockheed Martin end the document with a case study of 3 attempted intrusions, attempted by the same threat actor(s). The attackers had performed significant recon and were well prepared, however they're lack of multiple attack strategies resulted in their identification earlier & earlier, preventing their intrusion.

Overall I found this document to be highly informative. I found LM's advocation for reactive and proactive defense fascinating, effectively letting the same attackers make themselves easier to stop the more they tried to attack.
Cool idea.

PS: Here are some facts I found interesting from the article:
- PDFs & MS Office files (pptx, docx, etc.) are the most common types of files to be weaponised
- The three most prevalent delivery vectors observed by LM between 2004-2010 were email attachments, websites & USB removable media

## A)
Here's how I created a Virtual Machine running Debian Linux. Follow along!
To complete this process I used Tero Karvinen's article: Install Debian on Virtualbox

### Installing VirtualBox & Debian
I started by downloading the VirtualBox Software & Debian ISO to install the OS later:
Here are the links:
VirtualBox: https://www.virtualbox.org/wiki/Downloads
Debian: https://www.debian.org/CD/http-ftp/#mirrors

After completing the installation wizard for VirtualBox (Referred to as VB from now on) I was presented with this screen:
![image](https://github.com/user-attachments/assets/ea09fb8a-1541-4a5d-ab28-506b7762a175)

In this menu I clicked the 'New' button to begin setting up my virtual machine.

### Virtual Machine Setup

Afterwards, I was presented with this page, where I clicked the 'Expert Mode' button for increased control over how the VM was set up.
![image](https://github.com/user-attachments/assets/ac1dd87e-a89f-4562-917c-4310c60c052a)

In the next screen, I set a name for the VM, chose which ISO Image I would use (I used the Debian Image from the page linked earlier) and clicked the 'Skip Unattended Installation'
button. According to Tero's guide, installing 64-bit Debian was not possible otherwise.
![image](https://github.com/user-attachments/assets/4d8d126c-7ac3-485a-8b35-398469d07d5e)

Afterwards I dedicated 8GBs of RAM & 6 cores to the VM to ensure it ran smoothly. According to Tero's guide, you should allocate at least 4GBs of RAM and I personally wanted it to run as smooth as possible,
hence the processing power of 6 cores.
![image](https://github.com/user-attachments/assets/51be39b4-e559-4141-8c78-13ff33cc0a4b)

Finally, I allocated 60GB of storage space for the VM.
![image](https://github.com/user-attachments/assets/190a6e5b-d491-47aa-ad25-f0d25e8e042b)

I could now see the VM in the VB menu, but there was some last bits of setup left in the settings menu
![image](https://github.com/user-attachments/assets/f53b817a-3553-4ee4-88a2-ae2d6343041d)


![image](https://github.com/user-attachments/assets/68f703a3-69bd-4a79-9a83-7b1dc0b519c1)

Now that the VM was running, I chose the first option in the boot menu, 'Live System (amd64)
![image](https://github.com/user-attachments/assets/57a0ba55-70c3-42c8-a778-bd56a330f558)

It took a while to boot but waiting patiently was worth it, as the process had worked! However, I wasn't done.
![image](https://github.com/user-attachments/assets/41545458-f5e9-4c04-bc0f-a850ccd05522)

As recommended in Tero's guide, I ran a quick test to see if everything was working normally. From the top left 'Applications' menu I chose the web browser and navigated my way to GitHub.
There, I opened up this current draft of this assignment I'm writing. Meta, huh? Anyway, this tested that keyboard & mouse input worked, display output worked and that there was an internet connection.
![image](https://github.com/user-attachments/assets/5f752970-93c1-4442-9fd0-45cbe594f89f)

After this I started the Debian installer from the desktop. The software tried getting me to use American English (the horror!), but I quickly rectified the situation by instead selecting British English.
![image](https://github.com/user-attachments/assets/6d92034b-7926-4237-842a-4126cb490aa0)

I set my region to Europe, and my location to Helsinki. This is relevant as it determines the system's date and time. I subsequently selected my keyboard layout as Finnish.

Next, according to Kari's guide, the best option when it comes to partitioning your drive is the 'Erase Disk' option, so I checked. it Blind loyalty has always been a strong suit of mine.
![image](https://github.com/user-attachments/assets/abc5d35f-f040-4f2b-b006-e3e2e5c2c277)

After this I created my user for the VM. For the password I used an example Kari uses a lot during class. Can you guess it? (Hint, it's a starchy root vegetable and some numbers.)
![image](https://github.com/user-attachments/assets/a4234bd0-79c0-4b90-a194-dadda06e01aa)

After checking everything was OK in the summary, it was time to install. This took a while, so I made a sandwich and some tea.
![image](https://github.com/user-attachments/assets/cb4a76b9-1649-41b7-8e9d-9ca096e4b8f6)

Once the installation was all done, the VM rebooted, and I got a prompt asking for login info.
![image](https://github.com/user-attachments/assets/5e4e20f6-25c9-48ac-a90f-3266159ff117)


Aaaaaaand I was in!
![image](https://github.com/user-attachments/assets/16623aaf-3dd5-4898-99c9-83ce209d1e93)

Time to do the browser one last time:
Did it work?

![image](https://github.com/user-attachments/assets/982cc442-2b3e-484e-ac4e-6cd44fca6388)

Yes, it did. 
Done! A Debian VM, installed and ready to go. Many thanks to Kari for the very helpful guide.

# Optional Bonuses

## B) 
After this, I used the command
`$ sudo apt-get update`
To update all software on my VM

![image](https://github.com/user-attachments/assets/55b502a4-408e-456c-97a2-3ccff8182db8)


## C)
To install an Apache 2 server on my VM, I used the following commands from Reintech's article:
 1. `$ sudo apt update`
 2. `$ sudo apt upgrade` This took a while
 3. `$ sudo apt install apache2`
 4. `$ sudo systemcl status apache2`
 5. `$ sudo ufw allow 'Apache'`
 6. `$ sudo ufw reload`
 7. `$ sudo systemctl stop apache2`
 8. `$ sudo systemctl start apache2`
 9. `$ sudo systemctl enable apache2`
     
Command 4 didn't work me, so I had to install ufw

![image](https://github.com/user-attachments/assets/b5b77d02-5133-4b33-9ef8-fcc2f7b1155f)

Command 5 also didn't work, so I used a trick from stackoverflow to create the profile myself:
First, I ran this code `$ sudo apt-get -y install gedit`, then
`$ sudo gedit /etc/ufw/applications.d/apache2-utils.ufw.profile`
![image](https://github.com/user-attachments/assets/5de3f05e-0062-49f7-8cb8-2b7206e88666)

This opened this text editor, which i filled with this information and saved:
[Apache]
title=Web Server
description=Apache v2 is the next generation of the omnipresent Apache web server.
ports=80/tcp

[Apache Secure]
title=Web Server (HTTPS)
description=Apache v2 is the next generation of the omnipresent Apache web server.
ports=443/tcp

[Apache Full]
title=Web Server (HTTP,HTTPS)
description=Apache v2 is the next generation of the omnipresent Apache web server.
ports=80,443/tcp

![image](https://github.com/user-attachments/assets/d66f8c90-2e07-4f9f-891c-69c6c3cdb693)


## D)

First, I had to install netcat. I did so with this command `$ sudo apt-get install -y netcat-openbsd`

Afterwards, I chose to download example.com, using the command `$ sudo nc example.com 80`, which gave me this result:
![image](https://github.com/user-attachments/assets/22f77244-a4a2-4e2e-af97-3ac016fab07d)


## E)

Here are the logs of me downloading the website. I used the command `$ sudo journalctl -- since "5 minutes ago"` to find them in the terminal.


![image](https://github.com/user-attachments/assets/70a3fcde-2506-401a-8d62-ba7396c06f45)

![image](https://github.com/user-attachments/assets/d4913874-501d-44b4-8f51-8d084ebb6c84)

## F)


If the Kill Chain provides defenders with the next logical steps they need to take to make an intrusion and complete their objective,
Mitre's ATT&CK-framework provides a detailed description of actions they may take in each step. In the framework there are 14 different categories of actions, called 'tactics', such as reconnaisance, defense evasion, lateral movement etc. These tactics are further broken down into 'techniques', which provide details on what attackers need to do in order to utilise these techniques and tactics.

The Kill Chain offers a broader view of the situation, and ATT&CK (which stands for Adverserial Tactics, Techniques & Common Knowledge) provides a more in-depth look into exactly **how** attackers will attack.
I don't really think one is better than the other because if combined, then you're even better off!



## Sources
Arthur Codex, 2024: https://reintech.io/blog/installing-apache-on-debian-12-step-by-step-guide

Hutchins et al, 2011: https://lockheedmartin.com/content/dam/lockheed-martin/rms/documents/cyber/LM-White-Paper-Intel-Driven-Defense.pdf

Tero Karvinen, 2024: https://terokarvinen.com/information-security/

Tero Karvinen, 2023: https://terokarvinen.com/2021/install-debian-on-virtualbox/

Serverfault, 2023: https://serverfault.com/questions/1148725/where-is-some-os-logs-in-debian-12#:~:text=In%20Debian%2012%2C%20the%20traditional,accessible%20using%20the%20journalctl%20command.

Stackoverflow, 2018: https://stackoverflow.com/questions/51537084/i-installed-apache-2-but-in-sudo-ufw-app-list-there-is-no-apache-applications-in

Stackoverflow, 2012: https://stackoverflow.com/questions/11948245/markdown-to-create-pages-and-table-of-contents

Superuser, 2012: https://superuser.com/questions/506569/how-to-download-a-url-from-internet-by-netcat


