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

## d)

## e)

## Sources
