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
Next up was SQLZoo. I've done the Haaga-Helia databases courses but my SQL was a bit rusty so this was a good warmup for part m).
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
Alright, time for some *hacking*
In all seriousness, nice to do some SQLi after just writing queries.
Here's the starting screen:
<img width="756" alt="image" src="https://github.com/user-attachments/assets/bcf3a80a-080d-44f4-b0eb-008a95668691">

After logging in, we're greeted by a mock website's home page:
<img width="1269" alt="image" src="https://github.com/user-attachments/assets/b0348209-8057-402c-a62e-2ea591b55d0b">

I first investigated the site for any possible inputs but found none. I looked at the URL and realised it had a category= field meaning that the displayed page was coming from the url!
A quick 'or 1=1' and we were in :)
<img width="1246" alt="image" src="https://github.com/user-attachments/assets/b9b1f248-fcfe-40ab-9cec-79ec0ca4e62a">


## m)
## n)
## o)

## Sources
