# Week 5 Homework - Uryyb, Greb!
## By Benjamin Worton
Fun fact: the title, when decrypted, is 'Hello, Tero!'
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

**Steganography** serves to hide secret messages in other messages, such that the secret's very existence is concealed.
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
Okay, so initially I tried following along with Tero's guide, but my Linux was being very grumpy, so I chose to just do it on my Mac instead, whilst still trying to follow the guide as much as possible.

Downloaded gpg with Homebrew:
```
brew install gnupg
```
After the initial steps of creating a key I made sure it was working:

<img width="464" alt="image" src="https://github.com/user-attachments/assets/41202ac5-e442-4a5b-83c8-e25a5e90bf49">

I decided to use the same folder approach as the guide, and as I was listening to Trailer Park Boys whilst doing this assignment, named the folder Bubbles.

Public key generated for Bubbles:

<img width="440" alt="image" src="https://github.com/user-attachments/assets/b7316459-b8ed-4249-b396-ec97785df24b">

Imported my public key to Bubbles:

<img width="463" alt="image" src="https://github.com/user-attachments/assets/c48bd189-e600-4503-88e0-97887b3a4df7">

My public key signed by, full trust:

<img width="451" alt="image" src="https://github.com/user-attachments/assets/ff38a95b-5536-4b57-8492-6df357ca1359">

Next step was to repeat the process, but in reverse. Here I ran into the same issue I had with Linux:
The command 
```
cp -v folder/folder.pub
```
Just did not work. So I figured (already earlier with Linux, but doing this again) to just copy the file manually using the GUI into the parent folder, because the import command wouldn't work otherwise.

<img width="453" alt="image" src="https://github.com/user-attachments/assets/bbc72029-caf1-4438-803b-36b1bd46b57d">

AAAAA finally. Was stuck on this for way too long.

<img width="446" alt="image" src="https://github.com/user-attachments/assets/ecbfb856-9b0f-4ebb-acfd-070c0c982b69">

Signed, and ready. Time for the message:

<img width="771" alt="image" src="https://github.com/user-attachments/assets/e24ebce7-a924-4638-a340-0952f2f15613">

Message encrypted and ready to go:

<img width="481" alt="image" src="https://github.com/user-attachments/assets/1125a3e0-a38c-4166-8607-b347b4b222cd">

Again instead of using the command to copy the file, I did it manually by copying and dragging it to the correct folder.

Moment of truth:

<img width="742" alt="image" src="https://github.com/user-attachments/assets/34574637-b970-4ed2-b5c7-b6770d958b48">

It worked! That's such a relief. I ended up pretty much doing this twice, which was a bit annoying, but the positive aspect of that is I got more practice in!



## b)

After reading some threads on Reddit I decided I'd give MacPass a go. MacPass is a MacOS port of KeePass, a free open source offline password manager.
I got the app from its GitHub repo (https://github.com/MacPass/MacPass/releases/tag/0.8.1)

The first step was to create a new DB for storing passwords. I created a fake user and it gave me some pretty robust options for creating a password:
<img width="964" alt="image" src="https://github.com/user-attachments/assets/3f99b9b0-95ba-4daa-aef9-d2859d7c4111">

This is some pretty nifty software! Access to it on my computer is protected by a password.

Password managers help against pwning attacks. Additionally, a lot of people use simple memorable passwords for websites which are easy to remember, but also easy to crack. No normal person will remember these ridiculously complex generated passwords by MacPass, so users don't end up reusing the same memorable passwords across multiple websites!

## m)

For this section is chose to try Age, which is a recent program which performs the same function of gpg

```
brew install age
```
First up, create a public key:

<img width="529" alt="image" src="https://github.com/user-attachments/assets/321fb4ab-ffeb-4bca-af9d-175c34c9e5dc">

You can see your private key by running the command

```
cat key.txt
```

Next I created a message file, age_message.txt:

<img width="557" alt="image" src="https://github.com/user-attachments/assets/ac2ec314-a85e-45c4-8060-0c5be68571d2">

In Age, you need to have a recipient before encryption is possible. 

I went back to trusty Bubbles to be my partner once more, and created him a public key too:

<img width="536" alt="image" src="https://github.com/user-attachments/assets/1d932f89-7f52-4667-b0ee-3bb0167c3e5a">

Then I go back to my desktop to encrypt a message for Bubbles:

<img width="779" alt="image" src="https://github.com/user-attachments/assets/b1661265-e159-47f8-8bd0-22fb23a943a2">

It creates an encrypted file, with an additional extension of .age:
<img width="389" alt="image" src="https://github.com/user-attachments/assets/0e6e5b71-7d35-4382-8eca-cb506269d069">

To decrypt the file, I need Bubbles' private key:

<img width="551" alt="image" src="https://github.com/user-attachments/assets/5f381e6d-8529-4617-bc94-f7573612b5c4">

I quickly moved over Bubbles' key file to the desktop to use and then it was simply a matter of decrypting the message:

<img width="537" alt="image" src="https://github.com/user-attachments/assets/151036c6-9d4b-4247-8db9-d70b2083fe9b">

And done! I chose Age based on recommendations online. Honestly, it was a lot less fiddly then gpg. It felt a lot more accessible compared to gpg with simpler logic.



## n)

For this assignment, I thought I'd bug my friend and asked him to be the other party. I thought we'd just use symmetrical encryption to make it more convenient.

I wrote out a message:

<img width="778" alt="image" src="https://github.com/user-attachments/assets/e2687e6f-771c-4a71-bd7d-fa8c3ecf1a21">

For the sake of simplicity, I encrypted it with rot13:

<img width="668" alt="image" src="https://github.com/user-attachments/assets/337bb365-fb55-4c03-8688-6f4827365289">

Then I wrote him a a very chill email:

<img width="593" alt="image" src="https://github.com/user-attachments/assets/0c84d0ae-4bdf-4c8a-bb71-8fc4b1fe4b64">

And I got a picture back confirming it arrived:

![image](https://github.com/user-attachments/assets/b3450779-2d8f-410f-8de5-44d0fc53190c)

He then decrypted the message, and here's the result:

![image](https://github.com/user-attachments/assets/fca02d50-5d45-45d8-b637-bba344364eb4)

This was a fun little exercise!







## o)

After some quick googling, I found a website that has the letter frequency for a bunch of languages! I'm studying French, so here's its letter frequency:

e s a i t n r u l o d c m p é v q f b g h j à x è y ê z ç ô ù â û î œ w k ï ë ü æ ñ

For comparison, here's (British) English:

e t a o i n s r h l d c u m f p g w y b v k x j q z

French has a much larger amount of written vowels due to different sounds being represented with accents, whereas in English the most common letter E is pronounced very differently depending on the etymological root of the word. These sounds are all however represented by the letter E unlike in French e, é, è, ê, ë.

I find it interesting that a majority of the first half of the most frequent letters between these languages are the same! This is just a hunch, but due to English taking in a bunch of loanwords from Norman French etc. it's (in my opinion) likely that the lexical similarity contributes to the rough correllation.


## p)

Alrighty, let's get started.

OpenSSH server is already installed:

<img width="683" alt="image" src="https://github.com/user-attachments/assets/4645189d-d99b-4191-b45c-f1f4bd28e0d8">

Here's confirmation it's running:

<img width="803" alt="image" src="https://github.com/user-attachments/assets/0056abe7-0f3a-429c-8589-26ac7b691055">

I also added a rule to allow it past the firewall:

<img width="570" alt="image" src="https://github.com/user-attachments/assets/9e9127a9-974c-4d47-95b8-c0b6b65f6e8f">


## q)

Cool, next step is to connect to this server. I'll connect to the server via my Mac.

Made myself a keypair:

<img width="517" alt="image" src="https://github.com/user-attachments/assets/96bc0db8-6ecc-49c8-a011-d99d51203d1f">

Got the server's IP:

<img width="1001" alt="image" src="https://github.com/user-attachments/assets/5861052e-9e42-47bf-901c-fcfe4d170a47">






## r)

I chose to look at the certificate for my own website for this task. Now to whomever is reading this, please don't go look at it! (reverse psychology and all that, I know, but I'm being sincere)
My website (as of September 2024, I'm in the process of remaking it currently) is currently quite dated, as I originally made it when I was just starting to learn HTML & CSS. Anyway, here's the certificate:
<img width="542" alt="image" src="https://github.com/user-attachments/assets/73e08d50-39a0-4837-adcf-3980c183fa43">

The current certificate expires on the 1st of December, 2024. There's 2 fingerprints here, one for the certificate and one for the private key.

## s)

Let's crack this cipher. The tips give us some info:
- M is in English
- Likely a simple substitution cipher
- Apparently not a caesar cipher or rot13. Caesar is X replaced by (X -> 3Y) in an array of 26, rot13 is just X replaced by (X -> 13Y).

Here's the ciphertext:
HDMH'B TH. KWU'YI AWR WSSTOTMJJK M OWQINYIMLIY! MB KWU BII, BTGPJI BUNBHTHUHTWA OTPDIYB OMA NI NYWLIA RTHD SYIEUIAOK MAMJKBTB. BII KWU MH DHHP://HIYWLMYCTAIA.OWG

Just looking at this string, it's clear the last part of this is a url. It seems like special characters such as . , / : ' are not included here.

Now I **could** do this on pen and paper, but I'm lazy. Everyone knows that peak efficiency is writing code to automate a problem instead of just solving the problem, so Python to the rescue.

First, find the most frequent letter. 

```
ciphertext = "HDMH'B TH. KWU'YI AWR WSSTOTMJJK M OWQINYIMLIY! MB KWU BII, BTGPJI BUNBHTHUHTWA OTPDIYB OMA NI NYWLIA RTHD SYIEUIAOK MAMJKBTB. BII KWU MH DHHP://HIYWLMYCTAIA.OWG"

def occurrences():
    filtered_text = ''.join(ciphertext.split())
    counter = Counter(filtered_text)
    most_common_chars = counter.most_common(6)
    for char, count in most_common_chars:
        print(f"The character '{char}' appears {count} times.")
    return [char for char, count in most_common_chars]
```
This code provides the most common characters. In order of frequency, I H M B T W.

Replacing these characters in the string with ETAOIN gives us:

IDAI'O II. KNU'YE ANR NSSIOIAJJK A ONQENYEALEY! AO KNU OEE, OIGPJE OUNOIIIUIINA OIPDEYO OAA NE NYNLEA RIID SYEEUEAOK AAAJKOIO. OEE KNU AI DIIP://IEYNLAYCIAEA.ONG

Comparing these 2 strings, I'm quite sure the last portion is "at http://(something).org"

So ETAOIN wasn't it, but it helped a bit.
This is just estimating at this point but in C I believe:
1. M = A
2. H = T
3. B = S
4. G = G
5. O = O
6. Y = R
7. I = E
8. K = Y
9. W = O

Let's test it out!
```
def new_replacement():
    replacements = {
        'M': 'A',
        'H': 'T',
        'B': 'S',
        'Y': 'R',
        'I': 'E',
        'K': 'Y',
        'W': 'O'
    }
    replaced_text = ciphertext
    for old_char, new_char in replacements.items():
        replaced_text = replaced_text.replace(old_char, new_char)
    print(replaced_text)

new_replacement()
```
and we get:

TDAT'S TT. YOU'RE AOR OSSTOTAJJY A OOQENREALER! AS YOU SEE, STGPJE SUNSTTTUTTOA OTPDERS OAA NE NROLEA RTTD SREEUEAOY AAAJYSTS. SEE YOU AT DTTP://TEROLARCTAEA.OOG

Wow! Not quite there yet, but it seems like my hunch was correct.
Here are the two strings next to each other for comparison:

HDMH'B TH. KWU'YI AWR WSSTOTMJJK M OWQINYIMLIY! MB KWU BII, BTGPJI BUNBHTHUHTWA OTPDIYB OMA NI NYWLIA RTHD SYIEUIAOK MAMJKBTB. BII KWU MH DHHP://HIYWLMYCTAIA.OWG

TDAT'S TT. YOU'RE AOR OSSTOTAJJY A OOQENREALER! AS YOU SEE, STGPJE SUNSTTTUTTOA OTPDERS OAA NE NROLEA RTTD SREEUEAOY AAAJYSTS. SEE YOU AT DTTP://TEROLARCTAEA.OOG

The url is clearly Tero's website (terokarvinen.com), so not a .org domain. This means O = C,  W = O & G = M.

I added newly decoded letters to the program to crack the message even further, and kept this up until I decoded the whole plaintext.

Done! The decrypted plaintext is:

THAT'S IT. YOU'RE NOW OFFICIALLY A CODEBREAKER! AS YOU SEE, SIMPLE SUBSTITUTION CIPHERS CAN BE BROKEN WITH FREQUENCY ANALYSIS. SEE YOU AT HTTP://TEROKARVINEN.COM

Here's the program in its finished state, with all the functions used to crack this:

```
from collections import Counter

ciphertext = "HDMH'B TH. KWU'YI AWR WSSTOTMJJK M OWQINYIMLIY! MB KWU BII, BTGPJI BUNBHTHUHTWA OTPDIYB OMA NI NYWLIA RTHD SYIEUIAOK MAMJKBTB. BII KWU MH DHHP://HIYWLMYCTAIA.OWG"

def occurrences():
    filtered_text = ''.join(ciphertext.split())
    counter = Counter(filtered_text)
    most_common_chars = counter.most_common(6)
    for char, count in most_common_chars:
        print(f"The character '{char}' appears {count} times.")
    return [char for char, count in most_common_chars]

def replacement():
    most_common_chars = occurrences()
    replacements = ['E', 'T', 'A', 'O', 'I', 'N']
    replaced_text = ciphertext
    for i, char in enumerate(most_common_chars):
        replaced_text = replaced_text.replace(char, replacements[i])
    print(replaced_text)

replacement()

def new_replacement():
    replacements = {
        'M': 'A',
        'H': 'T',
        'B': 'S',
        'Y': 'R',
        'I': 'E',
        'K': 'Y',
        'W': 'O',
        'A': 'N',
        'C': 'V',
        'D': 'H',
        'G': 'M',
        'L': 'K',
        'O': 'C',
        'T': 'I',
        'J': 'L',
        'R': 'W',
        'S': 'F',
        'Q': 'D',
        'N': 'B',
        'E': 'Q'
    }
    replaced_text = list(ciphertext)
    for i, char in enumerate(replaced_text):
        if char in replacements:
            replaced_text[i] = replacements[char]
    replaced_text = ''.join(replaced_text)
    print(replaced_text)

new_replacement()  
```

## t)

Here's a quick python script to test rot13:
```
import codecs
first_rot = codecs.encode('NEVERDECODEME', 'rot_13')
second_rot = codecs.encode(first_rot, 'rot_13')
print(first_rot, second_rot)
```

And here's the output:
```
ARIREQRPBQRZR NEVERDECODEME
```
Huh? Wha happun?
Well, the English alphabet contains 26 letters. Rot13 works by substituting the letters of the plaintext with the letter 13 positions ahead of it. If you repeat the process, you've gone in a loop!

## u)
## Sources
https://terokarvinen.com/2023/pgp-encrypt-sign-verify/

Schneier 2015: Applied Cryptography: 1. Foundations

https://github.com/MacPass/MacPass/releases/tag/0.8.1

https://letterfrequency.org/letter-frequency-by-language/

https://htmlpreview.github.io/?https://github.com/FiloSottile/age/blob/main/doc/age.1.html

https://tech.serhatteker.com/post/2022-12/encrypt-and-decrypt-files-with-ssh-part-4/
