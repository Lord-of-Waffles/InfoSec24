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

Symmetric algorithms are algos where E can be calculated from D, and vice-versa. In most symmetrical algorithms, the keys are the same.

Furthermore, there are 2 typos of symmetrical algorithms:
1. Stream algorithms/ciphers: Operate on a single bit/byte of P at a time
2. Block algorithms/ciphers: Operate on groups of bits, called **blocks**

Public key algorithms are designed so that the key used for E is different than the key used for D.
In these systems, the key for E is called the **public key** and the key for D is called the **private key**.

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

//finish later


### PGP - Send Encrypted and Signed Message - gpg

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
