# Week 5 Homework - Uryyb, Greb!
## By Benjamin Worton

# Table of Contents
-  [x)](#x)
-  [a)](#a) 
-  [b)](#b)
-  [m)](#m)
-  [n)](#n)
-  [o)](#o)
-  [p)](#p)
-  [q)](#q)
-  [r)](#r)
-  [s)](#s)
-  [t)](#t)
-  [u)](#u)
-  [Sources](#Sources)

## x)

### Applied Cryptography
The second task in the course so far of summarising a chapter from this book. As with the previous one, it's pretty dense and packed full of information.

First, some basics:

- A message is **plaintext**. The process is of disguising a message in such a way as to hide its substtance is encryption.
- An encrypted message is **ciphertext**.

Some shorthand explained:
- **P**/**M**: Plaintext/message
- **C**: Ciphertext
- **E**: Encryption function
- **D**: Decryption function
- **K**: Key

In addition to providing confidentiality, cryptography is often asked to do other jobs:
- Authentication
- Integrity
- Nonrepudiation

A cryptographic algorithm or **cipher** is the mathematical function used for encryption and decryption. There are generally 2 related functions, 1 for encryption & 1 for decryption.

If the security of an algorithm is based on keeping the way that algorithm works a secret, it is a restricted algorithm.
Restricted algorithms are enormously popular for low-security apps, though they omes with inherent flaws. They can't be used by large groups of users, since every time a user leaves the group, everyone else must switch to a different algorithm. They also do not allow for quality control or standardisation.

Modern cryptography solves this problem with a **key**. This key might be any one of a large number of values, with the value range being called a **keyspace**.

A **cryptosystem** is an algorithm, plus all possible plaintexts, ciphertexts & keys.

There are 2 general types of key-based algorithms:
1. Symmetric
2. Public Key (also called asymmetric)

Symmetrical algorithms are algos where E can be calculated from D, and vice-versa. In most symmetrical algorithms, the keys are the same.

Furthermore, there are 2 typos of symmetrical algorithms:
1. Stream algorithms/ciphers: Operate on a single bit/byte of P at a time
2. Block algorithms/ciphers: Operate on groups of bits, called **blocks**

Public key algorithms are designed so that the key used for encryption is different than the key used for decryption.
In these systems, the key for encryptiion is called the **public key** and the key for decryption is called the **private key**.

Cryptanalysis is the science of recovering the plaintext of a message, without access to the key. The loss of a key through noncryptanalytic means is called a **compromise**, and an attempted cryptanalysis is called an **attack**.

A fundamental assumption in cryptanalysis is that the secrecy must reside entirely in the key. If others can't break an algorithm, even with knowledge of how it works, then they certainly won't be able to break it without that knowledge.

There are 4 general types of cryptanalytic attacks:
1. Ciphertext-only attack
2. Known-plaintext attack
3. Chosen-plaintext attack
4. Adaptive-chosen-plaintext attack

In addition, there are 3 other less common attacks:
5. Chosen-ciphertext attack
6. Chosen-key attack
7. Rubber-hose attack

The best algorithms are the ones that have been made public, been attacked by cryptographers for years and are still unbreakable.

In general, there are different categories of breaking an algorithm:
1. Total Break
2. Global Deduction
3. Instance (or local) Deduction
4. Information Deduction

An algorithm is considered **unconditionally secure** if, no matter how much ciphertext a cryptanalyst has, there is not enough information to recover the plaintext.
Algorithms that cannot be broken with available resources, either current or future are considered **computationally secure**.

You can measure the complexity of an attack in different ways:
1. Data Complexity - The amount of data needed as input to the attack.
2. Processing Complexity - The time needed to perform the attack. This is often called the **work factor**.
3. Storage Requirements - The amount of money needed to do the attack.

Good cryptosystems are designed to be infeasible to break with the computing power that is expected to evolve many years in the future. (Computationally secure)

**Steganorgraphy** serves to hide secret messages in other messages, such that the secret's very existence is concealed.
More recently, people are hiding secret messages in graphic images. Replace the least significant bit of each byte of the image with bits of the message (Mimic functions)
I remember seeing these! Every now and then, social media accounts of game development studios use steganography in ARGs to build up hype for upcoming content, maybe the most famous one being the leadup to Sombra's release in Overwatch.

Next some more historical cryptography:

A **substitution cipher** is one in which each character in the plaintext is substituted for another character in the ciphertext. The receiver then inverts the substitution to decrypt the message.

In classical cryptography, there are 4 types of substitution cyphers:
1. Simple substitution cipher (or monoalphabetic cipher)
2. Homophonic
3. Polygram
4. Polyalphabetic

One famous substitution cipher is the **Caesar Cipher**, in which each plaintext character is replaced by the character three to the right modulo 26. So A -> D, B -> E etc.
**Rot13** (rotation by 13 places) is another famous substitution cipher, a variant of the Caesar cipher. I'll go into more detail in the voluntary bonus featuring it.

On the other hand, you have **transposition ciphers**, where the plaintext remains the same, but the order of characters is shuffled around.

The chapter then details a few more classical cryptography methods such as rotor machines, the most famous of which was the **engima machine** used by the germans during WW2 to encrypt communications for U-Boat orders. 

**XOR** or exclusive-or operation is a logical operator used in symmetrical algorithms for encryption but which is relatively easy to crack via brute force by counting occurrences.

The final three short topics in the chapter detail one-time pads (an encryption scheme with randomly generated keys), some cryptographic algorithms used by computers (DES, RSA, DSA) and a short paragraph of the author showing their notation for large numbers with the probabilities of very improbable situations.

All in all, informative, but quite long.


### PGP - Send Encrypted and Signed Message - gpg

The next part of this assignment summarises Tero's article on utilising PGP for encrypted communications.
Since this is a summary of the article I chose to not include all the CLI commands as that would just be copying the article.

The articles walks through the steps to set up encrypted comms between Alice & Tero.

The first step is to create the first user's (Tero) keypair, meaning PGP uses asymmetric encryption.

This is done by installing the GPG or GNU Privacy Guard software, and having it generate the keypair.

So in order for Alice to be able to send a message to Tero, she needs Tero's public key, meaning it needs to be exported. This is achieved with GPG.
They key can be viewed with a command, and it is in ASCII armour, a type of encryption, further encoded into base64.

For this article, Alice is simulated. This could be done by creating a different user on the OS, or by using another computer, but for the sake of simplicity Alice is simulated with a folder. I would feel pretty miserable if my entire existence could be relegated to being a directory, so I hope Alice at least has a positive outlook on the situation.

The next step is to generate a keypair for Alice using GPG. Now that both parties are ready to talk it's time to introduce them to each other.

The article goes on to explain that a public key is quite literally public. They can be found on webpages, unencrypted emails, basically anywhere you can share information. 
Tero's previously generated public key is imported into Alice (that sounds uncomfortable) and now the not-so-sentient folder is able to encrypt messages with it.
The Alice-folder can check if the key is legitimate by checking the key's fingerprint (or digital signature). This may be a good idea if the key has been received via insecure channels such as an unencrypted email. Alice then signs Tero's key to mark it as trusted, ensuring communications work.

Trust goes both ways, so now Tero has to repeat this process of importing Alice's exported key, verifying it and signing it. Trust: acquired, and now the pair have each other's keys and have verified they are legitimate. Now they can finally gossip in peace!

Alice wants to give Tero the local tea, so she writes out her message in plaintext and encrypts it using Tero's public key. Due to this being asymmetric encryption, the message can now only be decrypted by using Tero's private key. The message begins with **----BEGIN PGP MESSAGE----**, and ends with **----END PGP MESSAGE----**. Since the message is encrypted it can be sent over untrusted channels safely. Alice gives Tero the encrypted message, and Tero decrypts it with his private key.

The rest of the article is solutions for various possible problems. A good read, now on to the hands-on tasks.


## a)
## b)
## m)
## n)
## o)
## p)
## q)
## r)
## s)
## t)
## u)
## Sources
https://terokarvinen.com/2023/pgp-encrypt-sign-verify/
Schneier 2015: Applied Cryptography: 1. Foundations
