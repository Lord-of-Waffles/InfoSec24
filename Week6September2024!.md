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
  ## m)
  ## n)
  ## o)
  ## p)
