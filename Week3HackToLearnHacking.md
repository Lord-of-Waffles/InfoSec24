# Week 3 Homework - Hack to Learn Hacking
## By Benjamin Worton

## x)

### Presentation summary

I watched the presentation titled "Smoke and Mirrors: How to Hide in MS Azure" By Aled Mehta & Christian Philipov (link: https://www.youtube.com/watch?v=uvoV75Q7cqU&list=PLLvAhAn5sGfiB9AlEt2KD7H9Dnr6kbd64&index=8&ab_channel=Disobey)

The point of the presentation was to highlight how more value clouds now hold to attackers due to the increase in critical data stored in them. As an example, in November 2022 Microsoft identified 0 instances potential exfiltrations of data (meaning data being extracted by non-authorised users), whereas in June 2023, they identified ~475,000. In between April and May 2023 there were ~40 billion brute force attempts at cracking passwords, which was roughly 4000 attacks per second.
In addition, attacks are becoming more sophisticated

The presenters then expand on some specifics about MS Azure (Microsoft's cloud service) and which actions are logged:
1. MS Graph
2. Provisioning
3. **Sign-in**
4. **Audit**
5. Identity risk
6. Global Secure Access

Surprisingly, some APIs used in sign-in and audit actions do are not logged!

This poses a significant security risk. The presenters make a point of understanding the tools you use in your business. Running any telemtry data you get from processes through some kind of analysis software can help identify problems you didn't even know were happening.

### Command Line Basics Revisited - Karvinen 2020

This article provides a list of basic commands for command line interfaces, and explanations for each of them.

In the article Tero also provide

### Protocol Building Blocks


### Bitcoin



## a)
Here we go! I'm doing these levels in the virtual Debian machine installed last week.
<img width="1443" alt="image" src="https://github.com/user-attachments/assets/0fd67041-2771-4110-8f30-433463c767f4">

### Level 0
Need to be careful to do it on the right port:
<img width="1190" alt="image" src="https://github.com/user-attachments/assets/c424d33f-cb9e-4e61-a30c-2084d5053fbf">

And we're in!
<img width="1360" alt="image" src="https://github.com/user-attachments/assets/11499d30-a226-4dfb-ac22-1c85f4f6afc1">
### Level 1
With a few simple commands, completed :)
<img width="1365" alt="image" src="https://github.com/user-attachments/assets/5ece7065-8e36-4f96-8ba5-4428bfdf1360">

### Level 2

Entry successful
<img width="217" alt="image" src="https://github.com/user-attachments/assets/5f4e6fc9-f84d-400d-9a89-cb51705baebe">

Password found! (with some embarrassing typos...)
<img width="399" alt="image" src="https://github.com/user-attachments/assets/a651c1c3-c84f-42da-97d3-6fa9f84ffeb4">

### Level 3
Access granted!
<img width="206" alt="image" src="https://github.com/user-attachments/assets/9729bdf3-7732-41d4-9d23-436c6f61724f">

Success:
<img width="329" alt="image" src="https://github.com/user-attachments/assets/b30f3c80-7296-47a9-ba26-c67a6f1cc3ed">

### Level 4
Here we go:
<img width="188" alt="image" src="https://github.com/user-attachments/assets/30edaf5c-c2ea-48c5-a5bc-bfff96e13dc8">

Phew this one took a bit, but I solved it!
<img width="505" alt="image" src="https://github.com/user-attachments/assets/eaea14e7-fe13-457b-bb88-d1517d6826ef">


## b)

No interwebs, no connections
<img width="496" alt="image" src="https://github.com/user-attachments/assets/a03d4c92-1e56-4cab-a48d-e65525c5463c">

Here's what happens when there's a connection:

![image](https://github.com/user-attachments/assets/c75d2a89-d791-47e0-bb39-25bfacc30337)

Ping is a command that tracks the time it takes to send and receive a packet to a server. In this case, I pinged Google's DNS server and it took 329ms to send and receive a packet. 8.8.8.8 is their public IPv4 address.
It's pretty easy to determine from the error message why I couldn't ping to the server without a connection, I wasn't on tht internet (big mass of networks), therefore there was no way to connect to the specified address since it was not a local address.


## c)
Results:
<img width="1341" alt="image" src="https://github.com/user-attachments/assets/e02122a4-3925-4bd2-8b58-c589a4c832e4">

Analysis goes here

## d)
Results:
<img width="1226" alt="image" src="https://github.com/user-attachments/assets/e7133c40-232d-4add-a4f9-6f974e947eb8">

Analysis goes here
## e)
