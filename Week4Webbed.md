# Week 4 Homework - Webbed
## By Benjamin Worton

# Table of Contents
-  [x)](#x)
-  [a)](#a) 
-  [b)](#b)
-  [c)](#c)
-  [d)](#d)
-  [e)](#e)
-  [Sources](#Sources)

## x)
This assignment covers some of the most important security risks in OWASP's Top 10 (2021)
### Broken Access Control
Number 1 in OWASP's 2021 top 10 is Broken Access Control.

*What it means*

Access control enforces policy such that users cannot act outside of their intended permissions.
Broken access control means that an attacker is able to elevate their privileges in a system through an exploit.

*How to prevent it*

Access control is only effective in trusted server-side code or server-less API, where the attacker cannot modify the access control check or metadata:
Here a few steps to prevent it:
- Except for public resources, deny by default.
- Model access controls should enforce record ownership rather than accepting that the user can create, read, update, or delete any record.
- Log access control failures, alert admins when appropriate
  
*Attack example*

### Injection
Moving on to number 2: Injection.

*What it means*
An injection occurs when an attacker passes malicious code or queries to an interpreter through some kind of request, such as an input in a web interface.
One of the more common forms of an injection is by hiding a SQL query in a request, called a SQL injection or SQLi.

*How to prevent it*

One option is to use a safe API, avoiding using the interpreter entirely.

Another is to sanitise data so that no user inputted data is passed to the interpreter.

*Attack example*
String query = "Select \* FROM accounts WHERE custID=' " + request.getParameter("id") + "'";
Due to concatenating unfiltered user inputted data this query is vulnerable to injection which can lead to sever consequences.

### Security Misconfiguration
Next on the list is number 5: Security Misconfiguration.

*What it means*

Security Misconfiguration is a bit of an umbrella term meaning any type of lapse in judgement whilst setting up the security for a system.
This could be something like default logins for a service or account remaining unchanged (for example username: admin & password: admin) or
incorrectly configured permissions on a cloud service.

*How to prevent it*

- A repeatable hardening process. Basically a checklist of potential security flaws that can be used as a template for different modules of a system, so for example development, QA & production environments.
- No unnecessary features or compononents which may have unknown security risks. More pieces = more variables for security.

*Attack example*

### Vulnerable & Outdated Components
Finally, number 6: Vulnerable & Outdate Components.
*What it means*
Related to the previous item, the more pieces there are in a (security) puzzle, the harder it is to get the full picture.
If you're system is utilising a bunch of components from different sources, they are likely to not have been built to the same standard of security or even be up to date.

*How to prevent it*

Trim the fat. If you don't need it, get rid of it. Dependencies, frameworks & components that are unused present a security risk.
If they aren't being used, they probably aren't being updated. If they aren't being updated, then they're probably not up to date in security! The longer something is available,
the more people will be poking holes into it to see where it's at its weakest.

*Attack example*



## a)

No report needed!
    
## b)
Alright, let's get started.

## c)
Okie doke, time for an upgrade:
Instead of writing
    sudo apt-get update
I accidentally wrote
    sudo apt-get upgrade
Which basically automatically updated all the required software instead of first fetching me a list of updates before choosing to upgrade. Whoops!
Anyway, while that was going I went to make myself some coffe, and after a few minutes it was done:
<img width="639" alt="image" src="https://github.com/user-attachments/assets/78383b4e-6fd0-40ac-85f5-38563fff1d4d">

Next it was time for the OS upgrade:
    sudo apt-get dist-upgrade
This was much quicker
<img width="804" alt="image" src="https://github.com/user-attachments/assets/25bcc271-375f-48f9-87c7-3c5865377351">

A quick reboot and all up to date!



## d)
Next up was SQLZoo. I've done the Haaga-Helia databases courses but my SQL was a bit rusty so this was a good warmup for parts e) & m).
### 0 SELECT basics
Pretty simple, I got the correct results with the queries:
```
SELECT population
FROM world
WHERE name = 'Germany';

SELECT name, population
FROM world
WHERE name IN ('Sweden', 'Norway', 'Denmark');

SELECT name, area
FROM world
WHERE area BETWEEN 200000 AND 250000;
```
### 2 SELECT from WORLD
This was fun! It was nice getting to write some queries again after a while :)
Here's what I wrote:

```
SELECT name, continent, population
FROM world;

SELECT name
FROM world
WHERE population >= 200000000;

SELECT name, population / gdp AS per_capita_GDP
FROM world
WHERE population >= 200000000;

SELECT name, population / 1000000 AS pop_in_millions
FROM world
WHERE continent = 'South America';

SELECT name, population
FROM world
WHERE name IN ('France', 'Germany', 'Italy');

SELECT name
FROM world
WHERE name LIKE 'United%';

SELECT name, population, area
FROM world
WHERE population >= 250000000 OR area > 3000000;

SELECT name, population, area
FROM world
WHERE population >= 250000000 XOR area > 3000000;

SELECT name, round(population/1000000) AS population,
             round(gdp/1000000000) AS GDP
FROM world
WHERE continent = 'South America';

SELECT name, round(gdp/population, -3) as per_capita_gdp
FROM world
WHERE gdp > 1000000000000;

SELECT name, capital
FROM world
WHERE length(name) LIKE length(capital);

SELECT name, capital
FROM world
WHERE LEFT(name,1) LIKE LEFT(capital,1) AND name <> capital;

SELCT name
FROM world
WHERE name LIKE '%a%'
      AND name LIKE '%e%'
      AND name LIKE '%i%'
      AND name LIKE '%o%'
      AND name LIKE '%u%'
      AND name NOT LIKE '% %';
```

This was a fun assignment!
## e)
Alright, time for some *hacking*.

In all seriousness, it's nice to do some SQLi after just writing queries.
Here's the starting screen:
<img width="756" alt="image" src="https://github.com/user-attachments/assets/bcf3a80a-080d-44f4-b0eb-008a95668691">

After logging in, we're greeted by a mock website's home page:
<img width="1269" alt="image" src="https://github.com/user-attachments/assets/b0348209-8057-402c-a62e-2ea591b55d0b">

I first investigated the site for any possible inputs but found none. I looked at the URL and realised it had a category= field meaning that the displayed page was coming from the url!
A quick 'or 1=1' and we were in :)
<img width="1246" alt="image" src="https://github.com/user-attachments/assets/b9b1f248-fcfe-40ab-9cec-79ec0ca4e62a">

Really cool, enjoyed this one.
## m)
Aaaaalright. This one was the longest one by far. 
## n)

For the next PortSwigger labs, I decided to do one more SQLi lab:

<img width="835" alt="image" src="https://github.com/user-attachments/assets/e6c4b149-fcb5-454e-8542-776a8e7fdb36">

<img width="1268" alt="image" src="https://github.com/user-attachments/assets/899b167e-7f0f-495a-aacc-e10a780ab3b6">

And we're done! Interrupting the query with a comment to bypass the password worked :)

Next I moved on to a few cross site scripting labs:

<img width="852" alt="image" src="https://github.com/user-attachments/assets/2cdbee41-4213-4f1b-9052-f83ad83a90d2">

Finally I can input directly on the page!

<img width="973" alt="image" src="https://github.com/user-attachments/assets/065bd61b-5710-40cc-a244-d588847c72da">

Result:

<img width="897" alt="image" src="https://github.com/user-attachments/assets/6573c8be-7e4f-4e89-b5e7-7e74be199c26">

Alright, time for the last lab for this report:

<img width="842" alt="image" src="https://github.com/user-attachments/assets/a6afafd6-474d-4f9d-a31d-b52e1069e907">

Viewing a post on the site reveals the opportunity to add a comment, which will be our attack vector:

<img width="893" alt="image" src="https://github.com/user-attachments/assets/d2c3b89c-2e0c-4a3a-ab93-96be90ef1228">

<img width="946" alt="image" src="https://github.com/user-attachments/assets/f3749161-c748-45f5-85bd-1ba1d574f442">

After some creative writing we're done. It didn't like my website address, so I just removed it and it worked :)

<img width="627" alt="image" src="https://github.com/user-attachments/assets/b376a21d-b22e-472c-ac04-48b9d2dd9ea4">

This was a really fun exercise! I've liked this week's homework a lot since it's been more hands-on.

## o)
Last assignment! Let's get it done:

First up was to read Maciej Ceglowski's blog post. I related to some of the points he made in the post, as while I really like programming, I'm not some 9000 IQ Mensa's A-list genius when it comes to math,
so this seemed like a good challenge and a good opportunity to improve! In programming courses, math-based exercises have usually been the hardest for me.

I'm currently learning Python, and it's been my favourite language *by far*, so I'll be doing these exercises in Python. For this week I'm doing set 1.
### Challenge 1
Convert string 

```
49276d206b696c6c696e6720796f757220627261696e206c696b65206120706f69736f6e6f7573206d757368726f6f6d
```

to

```
SSdtIGtpbGxpbmcgeW91ciBicmFpbiBsaWtlIGEgcG9pc29ub3VzIG11c2hyb29t
```

I had absolutely no idea what I was doing, so stackoverflow to my rescue. Python has a base64 library for encoding and decoding (thank god), so the answer is relatively simple:

```
from base64 import b64encode

the_string = "49276d206b696c6c696e6720796f757220627261696e206c696b65206120706f69736f6e6f7573206d757368726f6f6d"
the_result = b64encode(bytes.fromhex(the_string))
print(the_result)
```




## Sources
