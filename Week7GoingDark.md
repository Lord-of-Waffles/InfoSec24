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
## b)
## c)
## d)
## Sources
