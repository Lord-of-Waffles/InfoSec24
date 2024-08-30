# Kill  Chain

## X) Document Summary - Intelligence Driven Computer Network Defense
In this document, employees at Lockheed Martin's analyse a major change in cybersecurity attack patterns and showcase
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

## A)
Here's how I created a Virtual Machine running Debian Linux. Follow along!
For reference followed this guide by Tero Karvinen

# Installing VirtualBox & Linux
I started by downloading the VirtualBox Software & Debian ISO to install the OS later:
Here are the links:
VirtualBox: https://www.virtualbox.org/wiki/Downloads
Debian: https://www.debian.org/CD/http-ftp/#mirrors

After completing the installation wizard for VirtualBox (Referred to as VB from now on) I was presented with this screen:
![image](https://github.com/user-attachments/assets/ea09fb8a-1541-4a5d-ab28-506b7762a175)
In this menu I clicked the 'New' button to begin setting up my virtual machine.
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












## Sources
