# Week 7 Homework - Going Dark
## By Benjamin Worton

# Table of Contents
-  [x)](#x)
-  [a)](#a) 
-  [b)](#b)
-  [c)](#c)
-  [d)](#d) 
-  [Sources](#Sources)

## Disclaimer

All material below is intended for educational purposes only. Browse Tor wisely & securely (if your local jurisdiction allows it), and don't attempt to do anything illegal while on the network. What's illegal there is illegal in real life.

## x)

### 7 Things You Should Know About Tor

The article, written by Cooper Quintin, details 7 facts about Tor (and subsequently discredits common misconceptions):

1. **It still works**. With proper operational security, it is still possible to remain anonymous using Tor.
2. **It's not just used by criminals**. People trying to avoid censorship, journalists doing research and organisations communicating securely are all examples of Tor users.
3. **Tor does not have a military backdoor**. Tor is open-source, and several audits of the software have not displayed possibilities of a backdoor.
4. **No-one in the US has been prosecuted for running a Tor relay**. Whilst legislation differs between countries, according to the publisher's knowwledge there have been no public cases.
5. **Tor is easy to use**. The software comes with a pre-configured browser reminiscent of clearnet browsers.
6. **Tor is not as slow as you think**. Whilst slower than a regular internet connection, the developers have improved the speed to be much faster than it has traditionally been.
7. **Tor is not foolproof**. Going back to point 1., proper operational security is needed. If the user is reckless they can be identified, so taking some basic steps such as using the Tor browser or Tails is useful.

### Hiding Behind the Keyboard: The Tor Browser

This summary is broken down into the chapters listed on the assignment page

#### Introduction

Tor is a famous software when it comes to browsing the internet anonymously. By hiding the user's IP address in outgoing packets it hides the user's location.
Additionally it is accessible, mimicing a normal browser such as Firefox or Chrome that many are already used to.

#### History and Intended Use of the Onion Router

The point of Tor is to allow anonymous communication through the internet. Whilst not originally intended, it also serves as a method for criminals to communicate anonymously.
It was initially developed by the US government, but today is open-source and usable by anyone.

#### How the Onion Router Works

Tor works by sending the user's encrypted traffic through a network of relays (kind of like routing in clearnet), which are run by individuals voluntarily. When it passes through a relay, the data is encrypted moreand more. When the traffic reaches the final relay, or "exit", it connects the user to their desired target via an unencrypted connection. Each relay does not know the path the data took to reach it other than the previous relay, making tracking difficult.

This chapter includes a figure showcasing countries by size, where size is daily Tor users per 100 000 internet users. Unsurprisingly countries with bigger populations are represented, but I was surprised to see countries like Italy using Tor so heavily!

The Tor browser is simply a modified version of the Firefox browser, making it easy to use for most users. As stated earlier, as it offers anonymity it is used by criminals to communicate anonymously.

#### Tracking Criminals using Tor

However, it is possible to find out people's identities. The FBI were able to take down a service hosting sexual content of minors by using an exploit in the Firefox browser, which the Tor brwoser was based on.
Additionally, as with any system, one of the major security flaws will always be the user. Consenting to sharing geolocation data, installing plugins that track your IP and scripts running on websites can compromise your indentity.

Other methods for indentifying users include:
- Controlling as many entry & exit nodes as possible in an attempt to correllate traffic
- The Man-in-the-middle attack in attempt to discern the user's IP

These methods require time, and time is money, so not every suspect is subjected to this level of investigation.


## a)

I installed Tor in class, here's roughly how the process went:

- I booted up my virtual machine and opened up the Tor project's website
- I downloaded the compressed folder containing the browser and dependencies. Alternatively a more secure way of doing this would be using a package manager through a terminal.
- I decompressed the folder

Then I simply navigated to the folder through terminal and launched the browser:
<img width="813" alt="image" src="https://github.com/user-attachments/assets/8f8ed1b9-c80b-40b5-b1c5-99dbdd2895ce">

Then you're ready to go!

## b)

Search Engine:
<img width="1392" alt="image" src="https://github.com/user-attachments/assets/b3bf23e8-f6c3-4aec-923d-c6b0fd6c3b8f">
This one is Ahmia, one that Tero showed us in class.

Marketplace:
<img width="1293" alt="image" src="https://github.com/user-attachments/assets/af7681fd-1393-4b78-a14e-6a4432287906">
Venus Marketplace, from a glimpse they're selling illegal drugs, stolen credit cards & devices and firearms.

Forum:
<img width="1397" alt="image" src="https://github.com/user-attachments/assets/3ff2e54a-95c1-4fe6-871d-c462a79b7f90">
DarkNetArmy. Forum posts included people selling PayPayl accounts, hacking tools, accounts for online video games etc.

CIA's website:
<img width="1368" alt="image" src="https://github.com/user-attachments/assets/42c50c5a-d697-4b60-8c92-659fda85ed81">
Kinda funny that this seems like a recruiting website :)

## c)

Okie doke! That was interesting, time to try a different browser. This time I decided to install I2p through the terminal following I2P's instructions:

First I ran these commands

```
sudo apt-get update
sudo apt-get install apt-transport-https lsb-release curl
```

```
echo "deb [signed-by=/usr/share/keyrings/i2p-archive-keyring.gpg] https://deb.i2p.net/ $(lsb_release -sc) main" \
  | sudo tee /etc/apt/sources.list.d/i2p.list
```

```
curl -o i2p-archive-keyring.gpg https://geti2p.net/_static/i2p-archive-keyring.gpg
```

```
gpg --keyid-format long --import --import-options show-only --with-fingerprint i2p-archive-keyring.gpg
```

After this command the output should be:

  7840 E761 0F28 B904 7535  49D7 67EC E560 5BCF 1346

Then:

```
sudo cp i2p-archive-keyring.gpg /usr/share/keyrings
```

```
sudo apt-get update
```

```
sudo apt-get install i2p i2p-keyring
```

And I2P is installed! Now all I need to is to run the command

```
i2prouter start
```

It's important not to run this with sudo!

After this there's a short setup:

<img width="1159" alt="image" src="https://github.com/user-attachments/assets/b8d24464-a980-456d-94ac-b9d37acb3932">

Donezo:

<img width="1205" alt="image" src="https://github.com/user-attachments/assets/74668c99-cdaf-4af5-a41e-ec719276a206">

I then setup my browser to use the I2P proxy.

<img width="1908" alt="image" src="https://github.com/user-attachments/assets/42919340-b7f0-49f7-bffd-f1aa225fc6f4">

<img width="1910" alt="image" src="https://github.com/user-attachments/assets/da789475-1bdb-4c03-9ffc-2c619faea2e3">

Here are some I2P websites:

<img width="1559" alt="image" src="https://github.com/user-attachments/assets/8d138441-ec3b-4a80-8afc-a21b8627a85e">

<img width="1397" alt="image" src="https://github.com/user-attachments/assets/1b0ca200-ccb5-4d9e-a733-48465c3aed6a">

Both seem to be forums, and I found both of these on the I2P home page.


## d)

Since I saw that Venus Marketplace accepts bitcoin, I thought I'd check that. No dice, no address that I could find.
So, I thought that I'd just look up "bitcoin addresses" and found this site called blockchair:

<img width="1397" alt="image" src="https://github.com/user-attachments/assets/68d51e2c-fda3-4996-8229-1563aa1ccb72">

I took the hash of the top account and put looked at the activity on a website called bitcoinexplorer, and the latest transaction was made 2 hours ago!

<img width="1287" alt="image" src="https://github.com/user-attachments/assets/86cb88f5-5b77-48c9-aaf0-f9cd62332265">




## Sources
I2P 2024: https://geti2p.net/en/download/debian

Karvinen 2024: https://terokarvinen.com/information-security/#h7-going-dark

Shaves & Bair 2016: https://learning.oreilly.com/library/view/hiding-behind-the/9780128033524/XHTML/B9780128033401000021/B9780128033401000021.xhtml#s0010

Quintin 2014: https://www.eff.org/deeplinks/2014/07/7-things-you-should-know-about-tor
