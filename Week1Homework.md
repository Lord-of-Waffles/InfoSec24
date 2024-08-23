# Information Security Week 1 Homework
## By: Benjamin Worton

### X)

**Threat modelling** is a process in which a system is analysed in order to determine its strengths & weaknesses commonly used in cybersecurity. It is a process recommended by the Threat Modelling Manifesto to be included in the initial design phase of a system in order for security to be built-in from the beginning, though continous repetion is advised to keep security up to date. But what is the security for?

**Values.** Specifically, things which an organisation has in their posession which have value.
Effective threat modelling is governed by 3 principles:

  * Fundamentals are general truths that enable successful threat modelling.
  * Patterns are commonly repeated, effective methods which contribute to the quality of the model and are encouraged.
  * Anti-patterns, as their name implies, are simply the exact opposite of Patterns. They are detrimental to the quality of models and should be avoided.

In threat modelling, there are **4** key questions which, through the process of being answered, provide a framework towards creating a secure system:
  1. What are we working on?
  2. What can go wrong?
  3. What are we going to do about it?
  4. Did we do a good enough job?

Here are some methods provided by the OWASP Foundation on how to answer these questions:

1. To effectively conduct threat modelling, one must first understand the system they are working with. Visualising the system using methods such as
   **DFD**s (data flow diagrams) or brainstorming with stakeholders are useful in providing understanding of the particular ins and outs of a system.
   
2. Identifying threats and risks can be done in numerous ways, but a popular one is a process developed by Microsoft employees called **STRIDE**, which stands for
   * **S**poofing **-** Impersonating someone in order to gain access to a system.
   * **T**ampering **-** Unauthorised modification to data.
   * **R**epudiation **-** Denying responsibility for an action by removing evidence.
   * **I**nformation Disclosure **-** Unathorised extraction of confidential data.
   * **D**enial of Service **-** Loss of ability to use service due to excessive failed log-in attempts.
   * **E**levation of Privileges **-** Unauthorised promotion of user's role to gain more access in system via newly acquired privileges.

3. Now that threats have been identified, how they are dealt with is the next question. To do this, we can consult another acronym-based process provided by Adam 
   Shostack: **META**
   * **M**itigate **-** Actively take steps to reduce the likelihood of an identified threat.
   * **E**liminate **-** Remove a feature which constitutes a high risk.
   * **T**ransfer **-** Shift responsibility to another entity.
   * **A**ccept **-** Do none of the above, as they are not valid. The risk/threat is accepted to be tolerable.
     
4. At the end, its important to consider whether the solutions devised in the previous phases are enough. Here a few important questions to ask:
   * Does the DFD accurately reflect the system?
   * Have all the threats been identified?
   * For each identified risk, has a response strategy been agreed upon?
   * Has the threat model been formally documented?
   * Can the agreed upon mitigations be tested?

---------------------------------------------------------------------------------------------------------------------------------------------------------------------------

For this assignment I listened to episode 29 of the Darknet Diaries.
The topic of this episode is the Stuxnet computer worm thought to be deployed by the government of the United States of America (not officially confirmed) in collaboration with Israel against Iran in order to sabotage their nuclear development program. Kim Zetter, an investigative journalist who has written a book on the subject, makes a guest appearance in this episode.

To summarise: during the episode it is alleged that either The CIA, Mossad or possible both managed to deploy the Stuxnet worm into the development facility of Iran's nuclear programme near a remote village called Natanz. The worm's purpose was to sabotage the programme by infecting control systems for centrifuges used for enriching uranium by executing highly sophisticated methods of damaging the equipment while it was running, all the while appearing as if the equipment was faulty, not deliberately sabotaged. However, due to earlier failures in smuggling the worm into the facility, changes were made to the version which finally made it into the facility that made it spread much faster and more efficiently than intended.

While it laid dormant in machines where it did not detect the equipment it was meant to destroy, its rapid spreading around the world lead to it being discovered by a company called Semantec. Semantec would take their discovery to the press, eventually leading to Iranians being able to correllate the problems at their facility with those the worm was capable of, and were able to remove it and continue their project. Neither the USA or Israel have acknowledged their involvement with the worm.

I found this episode to be fascinating and it got me hooked on the podcast. Stuxnet was a significant event as it marked the first (publicly) known attack on a foreign country using digital systems. In the context of threat modelling, it would be unfair to say the Iranians didn't account for this type of attack as it hadn't been done before, showcasing how threat modelling really is a constant process as attackers are intelligent human beings purposefully trying to break into systems. Towards the end of the episode the hosts bring up the point that the attack technically didn't constitute an act of war, and that depending on one's perspective such an attack either provoked further agression or hindered possible violence and save lives. I'll definitely be listening to more episodes.


### A)

Proofpoint, an American cybersecurity company provides a list of good cybersecurity practices to ensure security:
- Strong, unique passwords
- MFA or multi-factor authentication
- Keeping software and systems up to date
- Backing up data
- Using antivirus or antimalware software
- Being cautious of phishing attacks
- Securing wireless networks
- Educating yourself and others on cybersecurity basics
- Encrypting sensitive data
- Using firewalls

Cyberscurity is a constant process that requires conistent maintenance and awareness. By mainitaing good cyber hygiene, companies can assure their busienss runs uninterrupted.

### B)

Company: **Imaginary Solutions Inc.**

Imaginary Solutions, a startup unicorn often called the "Spotify of dental hygiene", provides customers with what they never knew they needed, but can't live without:
a monthly subscription service where the customer is sent 10 toothpicks each month, for only 14.99€/month.

The company has an internal network which it uses for business purposes. Access is separated into roles, administrative being highest. Good security hygience training provided during onboarding.

#### Question 1: What are we working on?
![image](https://github.com/user-attachments/assets/135e2ac5-da23-4998-8d40-9a49db62282e)

This is my DFD depicting how information related to the business is moving. Key assets include but are not limited to:
- Customer data
- Company financial data
- Employee data
- Access to company systems
  
This company's key assets (or **values**) essentially consist of confidential data generated or required by the business model.

In order to deliver each customer's ordered toothpicks each month, the company needs access to their address and personal information to ship the toothpicks.

Customers interact with the company via a website, on which they have an account where they input necessary personal information.
In doing so, customers trust that the company will keep their personal data safe. In the event of this information being accessed by unauthorised actors,
customers' trust in the company's ability to keep their information safe will lead to less customers, meaning less money for the company. Not good.


#### Question 2: What can go wrong?

To identify threats, I'll be using the STRIDE-process.

First, **spoofing**. In order to access internal company computers to extract confidental data, unauthorised actors may attempt to impersonate an employee.
One common way this may occur is emails or chat messages sent to unsuspecting employees from a compromised account where they may attempt a phishing attack.

- Most people are famous with the Nigerian prince email scam, but may be much less alert when a friend's or family member's account sends a message containing a link, even with knowledge of good practices. High risk.

**Tampering**. Disgruntled employees with administrator privileges could tamper with data leading to business operations being unable to be completed.

- More of a rare possibility than an inevitability. Company network privileges separated by position at company. Low risk.

If an attacker is able to infiltrate company computers, they may attempt **repudiation**, erasing logs recording their actions and thus removing evidence of their presence and actions.

- Due to the company's security standards, unauthorised access unlikely (but possible). Medium risk.

Other than being able to gain access to a computer, an attacker may attempt an SQL injection to extract data from the database with queries, an example of **information disclosure**.

Whilst the above examples showcase different scenarios of an attacker gaining access to internal systems, if an attacker simply wants to cause harm to a business without having to gain access to its internal network, they can **DDOS** the company's website (main customer touchpoint). This will render the company unable to take in new customers.

Finally, **elevation of privileges**. If information transferred between services is not securely encrypted, an attacker could change contents in an attempt to give themselves administrator privileges in the company's internal network.






#### Question 3: What are we going to do about it?

#### Question 4: Did we do a good enough job?




### Sources

Karvinen, T. 2024. Information Security Course. URL: https://terokarvinen.com/information-security/ Accessed: 21 August 2024

Braiterman et al. 2020. Threat modelling manifesto. URL: https://www.threatmodelingmanifesto.org/ Accessed: 21 August 2024

Shostack, A. 2022. Welcome to the Worlds Shortest Threat Modelling Course. 12 Online videos. URL: https://www.youtube.com/playlist?list=PLCVhBqLDKoOOZqKt74QI4pbDUnXSQo0nf Accessed: 21 August 2024

OWASP Cheat Sheet Series Team. 2021. Threat Modelling Cheat Sheet. URL: https://cheatsheetseries.owasp.org/cheatsheets/Threat_Modeling_Cheat_Sheet.html Accessed: 21 August 2024

Jack Rhysider. 2022. The Most Sophisticated Malware Ever Made (That We Know Of) Darknet Diaries Ep. 29: Stuxnet. URL: https://www.youtube.com/watch?v=9DCwyuH29SI Accessed: 20 August 2024

Proofpoint. 2024. What is Cyber Hygiene? URL: https://www.proofpoint.com/us/threat-reference/cyber-hygiene Accessed: 22 August 2024

