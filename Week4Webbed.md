# Week 4 Homework - Webbed
## By Benjamin Worton

# Table of Contents
-  [x)](#x)
-  [a)](#a) 
-  [b)](#b)
-  [c)](#c)
-  [d)](#d)
-  [e)](#e)
-  [m)](#m)
-  [n)](#n)
-  [o)](#o)
-  [Sources](#Sources)

## x)
This segment covers some of the most important security risks in OWASP's Top 10 (2021)
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

An application uses unverified data in a SQL query that accesses account info. Modifying the browsers parameter for the type of account can allow an attacker access due to data not being filtered.

### Injection
Moving on to number 2: Injection.

*What it means*
An injection occurs when an attacker passes malicious code or queries to an interpreter through some kind of request, such as an input in a web interface.
One of the more common forms of an injection is by hiding a SQL query in a request, called a SQL injection or SQLi.

*How to prevent it*

One option is to use a safe API, avoiding using the interpreter entirely.

Another is to sanitise data so that no user inputted data is passed to the interpreter.

*Attack example*

```
String query = "Select \* FROM accounts WHERE custID=' " + request.getParameter("id") + "'";
```

Due to concatenating unfiltered user inputted data this query is vulnerable to injection which can lead to severe consequences.

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

A cloud service provider has default sharing permissionsopen to the internet by other users, allowing sensitive data stored in the cloud to be accessed unintentionally.

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

Components in software typically have the same base level of privilege as if they were within the app. Accidental coding errors or intentional backdoors provide vectors for attacks.

## a)

No report needed!
    
## b)
Alright, let's get started. While running WebGoat I disconnected my computer from the internet as suggested.
![image](https://github.com/user-attachments/assets/1b86a23a-d7b5-470f-852a-def0de4b35fa)

These exercises were about using the browser's developer tools to complete the assignments. The instructions were for Chrome but everything worked fine in Firefox.
![image](https://github.com/user-attachments/assets/a5effa65-228c-4cd2-9774-7d5cd460e11d)

The first assignment was simply calling a function
![image](https://github.com/user-attachments/assets/1cf2fae8-6ff3-471e-b400-3414d92a0dbe)

And the second one was finding the correct answer by tracking network traffic in the dev tools

![image](https://github.com/user-attachments/assets/21464040-3a82-4f27-9940-4df969f028f9)

Pretty simple stuff, but a nice introduction to the fact that there are more to websites than meets the eye ;)





## c)
Okie doke, time for an upgrade:
Instead of writing

```
sudo apt-get update
```

I accidentally wrote

```
sudo apt-get upgrade
```

Which basically automatically updated all the required software instead of first fetching me a list of updates before choosing to upgrade. Whoops!
Anyway, while that was going I went to make myself some coffee, and after a few minutes it was done (the update, not the coffee):
<img width="639" alt="image" src="https://github.com/user-attachments/assets/78383b4e-6fd0-40ac-85f5-38563fff1d4d">

Next it was time for the OS upgrade:

```
sudo apt-get dist-upgrade
```

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

This was a fun assignment! I only realised afterwards that I think you only had to do the first 2 tasks. Whoops.
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
I wasn't quite sure about what parts of the Injection chapter in WebGoat we should do here since there was a section in the tips of this week's homework about doing only the introduction part but for b)?
Anyway, I decided to do the Intro, Advanced and XSS sections.

The Intro part wasn't too hard. I enjoyed the exercises (they ended up being good practice for later) and got through it rather quickly 
![image](https://github.com/user-attachments/assets/6fb98c4b-adf4-45a1-9fb8-e7ef8e1544b4)

It was at the advanced part that it got difficult. I solved the majority of them on my own, but for the last one I had to look up some help.
With a lot of these assignments in WebGoat and PortSwigger, when I checked how others had completed them they were using different tools like burp suite etc to track how information was moving between the front & back-end of the site, but I was just doing everything directly on the site. 

![image](https://github.com/user-attachments/assets/e59648ba-b071-4d7d-af0f-8170cb1519b5)

I was kind of done with SQL for this week so decided to use the XSS portions, skipping from mitigation. These exercises turned to be kind of similar to the portswigger ones, so trying to find any kind of input field where the data wasn't filtered before being interpreted.

All in all a bit more theory than PortSwigger but still fun!

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

I'm currently learning Python, and it's been my favourite language *by far*, so I'll be doing these exercises in Python. For this week I did the first 2 assignments for set 1. I wasn't sure if we have to the whole set but as I had a bit of a busy week and this report was already long enough I thought it'd be fine :)
### Challenge 1

I had absolutely no idea what I was doing, so stackoverflow to the rescue. Python has a base64 library for encoding and decoding (thank god), so the answer is relatively simple:

```
from base64 import b64encode

the_string = "49276d206b696c6c696e6720796f757220627261696e206c696b65206120706f69736f6e6f7573206d757368726f6f6d"
the_result = b64encode(bytes.fromhex(the_string))
print(the_result)
```

### Challenge 2

This one was a bit harder. I had to look up how to do XOR in Python, but I got there in the end!
```
import binascii

def fixed_XOR():
    s = "1c0111001f010100061a024b53535009181c"
    x = "686974207468652062756c6c277320657965"

    s_bytes = bytes.fromhex(s)
    x_bytes = bytes.fromhex(x)
    result = bytes([b1 ^ b2 for b1, b2 in zip(s_bytes, x_bytes)])
    result_hex = binascii.hexlify(result).decode('utf-8')

    return result_hex
 
print(fixed_XOR())
```

## Sources
BentleySec, 2024: https://bentleysec.com/webgoat/Injection_advanced.html

Karvinen, 2023: https://terokarvinen.com/2023/webgoat-2023-4-ethical-web-hacking/

Karvinen, 2024: https://terokarvinen.com/information-security/#h4-webbed

OWASP, 2021: https://owasp.org/Top10/

Rompay, 2024: https://cedricvanrompay.gitlab.io/cryptopals/challenges/01-to-08.html
