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
One-Way functions:

A one-way function would be something like  func(x) = x

It is easy to understand the output when you have the input, but the reverse is much harder.  

While one-way functions are not protocols, many commonly used protocols used in modern cryptography utilise one-way functions, such as:
- Trapdoor one-way function: special type of one-way function with a secret trapdoor. If you know the secret, you can easily compute the function in reverse.
- A one-way hash function: function that takes a variable length input string (called a pre-image) and converts it to a fixed-length (generally smaller) output string (called a has value)

The point of a hash function is to fingerprint an image; To produce a value that indicates whether a candidate pre-image is likely to be the same as the real pre-image.


The latter part of the chapter provides methods of creating authentic digital signatures:
- A symmetric cryptosystem & an arbitrator
- Public key cryptography
- Digital Signature Trees - used in bitcoin!
- public key cryptography + one-way hash functions

  ## a)
Okie doke, first step is to install Hashcat. I'm following along with Tero's article: Cracking Passwords with Hashcat, you can find the commands used there.

A quick updating of packages, and Hashcat is installed. For this assignment I'm using the rockyou.txt file.

![image](https://github.com/user-attachments/assets/8b1481f4-2ff3-4861-b6b9-387ea7e16ea0)

Over 14 million words! That's a long list.
I give Hashcat a hash to crack:

![image](https://github.com/user-attachments/assets/2c5cc9e9-ddde-480c-8c57-d383c7a063c3)

I get a pretty long output: ![image](https://github.com/user-attachments/assets/02a316b6-078c-4bac-9640-151f6e19e6b5)

This command stored the output of the cracking in the "solved" file:
![image](https://github.com/user-attachments/assets/5d77f62d-ae78-4bad-9674-98a764c54c54)

According to the article, you really should do this on the host, not a VM. That way you're able to utilise the GPU properly to speed this process up!

  ## b)

So that's what I did! First step is again to install Hashcat, but this time on my host machine which is running Windows.
I chose downloaded the binaries version from their website:

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
  ## n)
  ## o)
  ## p)
