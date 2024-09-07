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

This was a really useful resource for the later assignments especially a)!

These commands are used for manoeuvring around a computer's file directories and manipulating data.
They can also be used to connect to remote servers where you can use the same commands to interact with that server's data & directories.

I've also found the terminal to be a nice and quick way of installing software by using Homebrew. I really recommend it!


### Protocol Building Blocks

This chapter details different types of protocols in modern cryptography. While quite long, it was packed full of theory for a topic I've wanted to learn more about for quite a while.

Firstly: What's a protocol?
A protocol is a series of steps, involving two or more parties, designed to accomplish a task. 
They abstract the process of accomplishing a task from the mechanism by which the task is accomplished.

As can be extrapolated from the name, a cryptographic protocol is a protocol that uses cryptography, involving some cryptographic algorithm.
A simple goal for a cryptographic protocol is the it should not be possible to do or learn more than what is specified in the protocol.

There are a few other types of protocols:
- Arbitrated Protocol: Comprised of 3 parties, the 2 main parties and an arbitrator (disintrested third party trusted to complete a protocol)
- Abjudicated Protocol: In addition to the 2 main parties, in the even of a dispute the outcome of the protocol is determined by a third party, an abjudicator (likea judge in a court case)
- Self-Enforcing Protocol: Only 2 main parties, no third party required. The protocol is constructed so that there cannot be any disputes. If one of the parties tries to cheat it is immediately detected and the protocol stops.

But it isn't as simple as you'd think, because protocols can be influenced. Attacks are classified into passive and active attacks:
- Passive: Someone not involved in the prtocol can eavesdrop on some or all of the protocol.
- Active: An attacker can try to alter the protocol to their own advantage by for example: manipulating previous messages, posing as someone else, manipulating stored information etc.

It is also possible that the attacker could be on of the parties involved in the protocol, called a cheater:
- Passive cheaters follow the protocol, but try to obtain more information than the protocol intends them to.
- Active cheaters disrupt the protocol in progress in an attempt to cheat.

Cryptosystems:

A good cryptosystem is one in which all the security is inherent in knowledge of the key and none is inherent in knowledge of the algorithm.

There are 3 types of cryptosystems:
1. Symmetric cryptosystems - Same key used for both encrypting and decrypting messages
2. Public key cryptosystems - Messages are encrypted using receivers public key, but can only be decrypted by their private key, which only the receiver can access.
3. Hybrid cryptosystems - Since symmetric cryptosystems are faster than public key ones but not as secure, a public key cryptosystem is used to create a session key between the communicating parties, which is then sent using symmetric encryption.

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

All in all an interesting read, if a bit long. Was good to catch me up on some cryptography basic theory before diving into the Bitcoin paper!


### Bitcoin

In this paper, the concept for cryptocurrencies is introduced.

The author, going by the name Satoshi Nakamoto (they have never publicly revealed themselves, so this alias is not considered by all to by the author's real name), presents their case as to why an electronic payment system based on cryptographic proof is needed, instead of more traditional trust based methods such as banks. This system would allow any two willing parties to transact directly with each other without the need for a trusted third party.

The currency would be (is) an electronic "coin", or a chain of digital signatures. Each owner transfers the coin to the next owner by digitally signing a hash of the previous transaction and the public key of the next owner and adding those to the end of the coin. Ownership can be verified by verifying the signatures on the chain.

But there's a problem: A payee can't verify that one of the owners did not double-spend the cash.

If you were to introduce a trusted central authority (such as a bank) the fate of the entire monetary system depends on the authority's actions. Not the best. What else?

Transactions are public announced using a timestamp server:
- A timestamp server works by taking a hash of a block of items to be timestamped and widely publishing the hash. The timestamp proves that the data must have existed at the time in order to get into the hash.

Next: proof-of-work:
Proof-of-work involves scanning for a value that when hashed, such as with an algorithm such as SHA-256 (developed by the NSA!), the hash begins  with a number of zero bits. The average work required is exponential in the number of zero bits required and can be verified by executing a single hash. Proof-of-work is essentially a one-CPU-one-vote system. The system is secure as long as honest nodes performing the proof-of-work calculations collectively control more CPU power than any cooperating group of attacker nodes.

Here's how this network is run:
1. New transactions are broadcast to all nodes
2. Each node collects new transactions into a block
3. Each node works on finding a difficult proof-of-work for its block
4. When a node finds a proof-of-work, it broadcasts the block to all needs
5. Nodes accept the block only if all transactions in it are valid and not already spent
6. Nodes express their acceptance of the block by working on creating the next block in the chain, using the hash of the accepted block as the previous block

##### Here are some other bits of knowledge from the document I couldn't really figure out a category for, but felt were important:

Nodes consider the longest chain to be the correct one and will keep working on extending it.

By convention the first transaction in a block is a special transaction that starts a new coin owned by the creator of the block. This adds an incentive for nodes to support the network, and provides a way to initially distribute coints into circulation, since there is no central authority to issue them.

The steady addition new coins is analogous to gold miners expending resources to add gold to circulation.

The incentive may help encourage nodes to stay honest. If a greedy attacker is able to assemble more CPU power than all the honest nodes, he would have to choose between using it to defraud people by stealing back his payments, or using it to generate new coins. They will most likely find it more profitable to play by the rules which favour them with more new coins than everyone else combined, instead of undermining the system and subsequently, their wealth.

Older block are archived using digital signature trees to save disk space. 

To allow value to be split and combined, transactions contain multiple inputs & outputs.

The traditional banking model achieves a level of privacy by limiting access to information to the parties involved and the trusted third party.



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

Phew this one took a bit of thinking, but I solved it!
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
