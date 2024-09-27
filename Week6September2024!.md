# Week 6 Homework - September2024!
## By Benjamin Worton

# Table of Contents
-  [x)](#x)
-  [a)](#a) 
-  [b)](#b)
-  [m)](#m)
-  [n)](#n)
-  [o)](#o)
-  [p)](#p)
-  [Sources](#Sources)

  ## x)
I had actually already read and summarised this chapter for the course's third week's homework! Here's what I wrote then:

### One-Way functions:

A one-way function would be something like  func(x) = x

It is easy to understand the output when you have the input, but the reverse is much harder.  

While one-way functions are not protocols, many commonly used protocols used in modern cryptography utilise one-way functions, such as:
- Trapdoor one-way function: special type of one-way function with a secret trapdoor. If you know the secret, you can easily compute the function in reverse.
- A one-way hash function: function that takes a variable length input string (called a pre-image) and converts it to a fixed-length (generally smaller) output string (called a has value)

### One way hash functions

The point of a hash function is to fingerprint an image; To produce a value that indicates whether a candidate pre-image is likely to be the same as the real pre-image.


The latter part of the chapter provides methods of creating authentic digital signatures:
- A symmetric cryptosystem & an arbitrator
- Public key cryptography
- Digital Signature Trees - used in bitcoin!
- public key cryptography + one-way hash functions

  ## a)
Okie doke, first step is to install Hashcat. I'm following along with Tero's article: Cracking Passwords with Hashcat, you can find the commands used there. As with other weeks' assignments, I don't want to just copy his article word-for-word with all the commands, that would just be copying.

A quick updating of packages, and Hashcat is installed. For this assignment I'm using the rockyou.txt file.

![image](https://github.com/user-attachments/assets/8b1481f4-2ff3-4861-b6b9-387ea7e16ea0)

Over 14 million words! That's a long list.
I give Hashcat a hash to crack:

![image](https://github.com/user-attachments/assets/2c5cc9e9-ddde-480c-8c57-d383c7a063c3)

I get a pretty long output: ![image](https://github.com/user-attachments/assets/02a316b6-078c-4bac-9640-151f6e19e6b5)

This command stored the output of the cracking in the "solved" file:
![image](https://github.com/user-attachments/assets/5d77f62d-ae78-4bad-9674-98a764c54c54)

According to the article, you really should do this on the host, not a VM. That way you're able to utilise the GPU properly to speed this process up...

  ## b)

So that's what I did! First step is again to install Hashcat, but this time on my host machine which is running Windows.
I downloaded the binaries version from their website:

![image](https://github.com/user-attachments/assets/e20a0412-2d2e-4e32-8dd3-dee8a5c1b3f3)

Then the CUDA Toolkit from Nvidia:

![image](https://github.com/user-attachments/assets/7014c95b-b473-4f50-8fb7-7b4f5d7c6db2)

After clicking through the CUDA installer, waiting for it to install for what felt like half an hour, and extracting the hashcat zip file it was time to test if it had worked:

![image](https://github.com/user-attachments/assets/ed1faded-963d-4678-af91-6692b3a0055b)

All good, ready to get going.

For this assignment I need to crack the hash
```
d595b2086532422bbe654bc07ea030df
```
Huh, why isn't hashid working? Because it's its own software, right. I need python to install it too. Time to install those as well:

![image](https://github.com/user-attachments/assets/09f936d8-bb2c-4138-bbe5-cefbb41fbab2)

Windows was trying to run python from the Microsoft store, so had to disable that.
Had to manually add python to my path as well. Thanks Microsoft.

![image](https://github.com/user-attachments/assets/016545ac-8673-4639-a2fa-d9dd501507a6)

I also installed the rockyou.txt file using this command:

```
curl -L -o rockyou.txt.tar.gz https://github.com/danielmiessler/SecLists/raw/master/Passwords/Leaked-Databases/rockyou.txt.tar.gz
```
I had to move it to the same directory as hashcat.exe, but I finally got it to work.

Finally.


OK! Time to actually do the assignment.
Here's the hashid result:

![image](https://github.com/user-attachments/assets/78f50d28-5ffd-4ed4-a6a4-06cd4ddcce66)

First I thought I'd try MD5, since this hash is 32 characters long.

I ran this command:
```
hashcat -m 0 -a 0 d595b2086532422bbe654bc07ea030df rockyou.txt
```

Cracked. Here's the result:
![image](https://github.com/user-attachments/assets/2a6fee13-332e-4fed-bac7-5048f4ef42c7)

That took a while, but I got there in the end!

  ## m)
Another follow-along assignment, this time I'm following Kari's article: Crack File Password With John

This article teaches how to crack a file's password using a dictionary attack. Back to the Linux VM!

The first step was to make sure I had all the necessary software like Git installed, then download John the Ripper:

![image](https://github.com/user-attachments/assets/dde41a23-2196-4632-b66b-6cb06bec4a27)

And then compile it using ./configure and subsequently compile it with make -s clean && make -sj4:

![image](https://github.com/user-attachments/assets/a3d8c52b-0c3d-43f2-9a05-48cf5d1f1565)

![image](https://github.com/user-attachments/assets/74545008-41cc-4284-ae99-c1f3408981b8)

Donezo! The result was a **lot** of different scripts, here are just the first few:

![image](https://github.com/user-attachments/assets/9b1856f1-d139-4ff3-a8c8-1a0cc3666f6d)

I ran this really long command Tero had written on his article and got a pretty long output. I was getting some errors at the bottom, but the article said that if the output included a version number, it was working. Hooray?

![image](https://github.com/user-attachments/assets/7c950de8-d4d3-425e-8c6b-ace9a13b692c)

Next up was to download a sample .zip file to try and open it:

![image](https://github.com/user-attachments/assets/31579619-cb7e-4b7e-b42b-35b405aef68b)


No dice, needs a password. To get access I need to crack it. First I extract the hash:

![image](https://github.com/user-attachments/assets/d3c4b1fc-825a-42f9-837a-ed259c571fac)

Then I use John the Ripper to perform a dictionary attack against it:

![image](https://github.com/user-attachments/assets/384ec0c4-925f-4754-a561-d8f6259e04c3)

This gave us the password: butterfly. Then I try to unzip it again with the new password and read the file inside:

![image](https://github.com/user-attachments/assets/0ebd9d84-2756-47c4-8cf9-46f2042603ab)


This was pretty fun :)

  ## n)

So I've asked my friend to password protect a .zip file for me to crack, but it didn't work. I tried to make one myself, but it didn't work. I tried to crack both of them on linux and my host, installed Jack the Ripper and Hashcat on both, but no dice.

Something about the .zip passwords just hasn't worked. We tried setting passwords in 7zip and Windows itself, but nothing worked! Really unfortunate. It seems like it just encrypts the folder contents, not the folder itself.

![image](https://github.com/user-attachments/assets/3bc957d6-a1e0-4690-840a-170b36a42a8d)




  ## o)

(I did this before part n))
My friends cannot escape my pestering, so I had one create a different file that was password protected for me to crack.

This folder is .7z, so I needed some specific software to extract it:

![image](https://github.com/user-attachments/assets/f36f9f3b-46d2-4566-9002-0dd324a2006c)

![image](https://github.com/user-attachments/assets/004b93f9-1d0b-430d-b58b-5838216e0eed)

Oh dear, I don't have the password. Let's fix that. I had to install a module for the 7z script to work, and got the output to hash.txt:

![image](https://github.com/user-attachments/assets/a563b06b-36ad-4396-aa50-8807e08fc476)

Here's the hash in case you're curious:

![image](https://github.com/user-attachments/assets/24235325-492f-42e3-b549-56d770ddfb39)

Next I ran a dictionary attack against the hash.

Progress update mid process:

![image](https://github.com/user-attachments/assets/09fb2e8d-6dce-4a05-a9c4-7df928334c0a)

Trying all kinds of passwords:

![image](https://github.com/user-attachments/assets/1636d2d1-65be-40ea-9bcb-d52ed9af0d00)

At this point it was taking too long to crack, so it was time for a different attack. I closed the VM and booted up hashcat on my host machine to start cracking:

![image](https://github.com/user-attachments/assets/64feda53-425c-47a8-b4d3-93b2738018ab)

This was a **LOT** faster, but it was still taking some time. Turns out my friend had come up with a 17 character password, containing 2 words and 2 digits. Holy moly. Hashcat might've been able to crack this given an entire day, but unfortunately that wasn't an option for me. This just goes to show how effective a good password is!

Final progress status:

![image](https://github.com/user-attachments/assets/6015848e-2468-4d5d-91a3-587ef1faaf41)

  ## p)

This week's homework has been a bit weird. I had already summarised the first part, and 2 of the password cracking voluntary assignments didn't really work out. Luckily this one is a bit simpler: Summarising a presentation from Disobey 2019 by Alexander Forbes, a IBM security-team ethical hacker. He stresses that penetration testing ATMs without the owner's permission is an easy way to get into trouble. This summary is written only for educational purposes, don't go breaking the law.


### The first section is a brief history on ATMs:
- The market used to be more diverese with a lot of different manufacturers, nowadays they've consolidated into only about 4 separate companies.
- They use heavily standardised software

### Next is what they're made up of:
- Most modern ATMs are running 32-bit Windows 7/8, sometimes even Vista
- Peripherals mostly USB connected

### Standardisation:
- Usually a pretty stripped down OS with some whitelisting services
- Custom BIOS occurs sometimes, but not too common

### on-ATM Attack Surfaces (more back-end type protections):
- In event of back-end systems being compromised by attack, software has integrity checks to prevent remote exploit attacks
- Defenses for physical attacks include cameras, police, withdrawal limits.
- Mirrors in ATM corners to help customer see if they're being spied on

### ATM Attack Surfaces
- Needs to be well placed in line of sight to cameras and public places
- Alexander says one of the first questions his team asks when assessing an ATM is "what is the physical security like?"
- Most successful attacks are brute force attacks, heavy impacts, explosives etc.
- Networking security typically not as strong as physical due to perceived concept of security in ATMs being sufficiently removed from the internet, apparently the reality is quite the opposite.
- Gaining root access usually means game over for the bank
- A more modern type of attack is connecting customer hardware to monitor the system, swiping credit card numbers to be sold later

### Flaws in ATM defenses (physical):
- Heavy, but moveable with enough strength
- Built in public places, but not always monitored at night
- Frame is usually only thin metal with a plastic facade
- Locks to access internal components surprisingly pickable
- Network hardware sometimes able to be accessed from the exterior

### Flaws in ATM defense (networks):
- Impromper authentication in back-end and unsecure encryption surprisingly common
- Improper usage of firewalls
- Monitoring isn't always on point, short outages not investigated and logging data not always sent unless back-end is attacked

### Flaws in ATM defense (embedded systems):
- Many ATMs not setup to block booting from external media
- Drives hardly ever encrypted
- Organisations quite risk-averse. "If it ain't broke don't fix it"
- Misconfig in whitelisting

### Flaws in ATM defense (hardware):
- Authentication between different devices not always required between cash-dispenser and the software
- Not used at all between other devices
- USB connections prone to attacks
- Internals are designed to be easy to maintain, but tradeoff is that it's also easy to modify with lots of space


### Successful modern attacks:
- A majority are physical
- Most sophisticated attacks target the embedded systems or hardware
- Groups of malware that make the ATM spit out cash
- "Black box" attack by connecting malicious hardware with USB

### Attackers have to realise:
- When the machines are refilled, so as to not attack an empty target
- Not to empty out an entire machine, so as to alert suspicion
- CCTV will catch them
- Audio sensors will catch them
- Due to the nature of the crime, authorities are very invested in arresting the attacker, as are banks and insurers
- Physical money, at least a big amount of it, is heavy
- Laundering lots of money isn't so easy
- The rate the machine can spit out cash: best case 14-16 **minutes**

### Defenders have to realise:
- Listen to experts
- Use reliable vendors
- Ensure good physical installation of the machine (and whole disk encryption)
- Regular software updates, proper verification methods, very strict whitelisting


All in all, a weird week of homework with a bunch of problems. Learned a lot though!


# Sources

Disobey 2024: Jackpotting ATM's - Its easier than you might think - Alexander Forbes (https://www.youtube.com/watch?v=ThPJrPf7O2s&t=1s&ab_channel=Disobey)

Karvinen 2024: https://terokarvinen.com/information-security/#h6-september2024

Karvinen 2023: https://terokarvinen.com/2023/crack-file-password-with-john/

Karvinen 2022: https://terokarvinen.com/2022/cracking-passwords-with-hashcat/

Schneier 2015: Applied Cryptography: Chapter 2.3 & 2.4

Worton 2024: https://github.com/Lord-of-Waffles/InfoSec24/blob/main/Week3HackToLearnHacking.md Chapter x)






