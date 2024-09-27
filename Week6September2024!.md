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

According to the article, you really should do this on the host, not a VM. That way you're able to utilise the GPU properly to speed this process up...

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

In line with last week's homework, I decided to pester my friends once again, and asked my friend to create a password-protected zip file for me to crack!

I moved the folder from my host machine to my virtual machine via a shared folder.

![image](https://github.com/user-attachments/assets/082d2758-d087-4dbc-940b-1ab9a45458ca)

second secret folder.zip is the file I'm cracking here, secret folder is a .7z for the next section :)

(I had to add underscores so I could access the files in the terminal)




  ## o)

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

This was a **LOT** faster.


  ## p)
