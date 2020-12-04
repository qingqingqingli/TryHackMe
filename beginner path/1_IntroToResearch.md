# Introduction to research

Information Security and Computer Science rely heavily on researching different concepts and learning how things work. You need to build a good methodology to research questions when you hit an obstacle, and this is what this section is all about.

## Tutorial

On TryHackMe you'll learn by deploying and hacking virtual machines. AttackBox is a web-based machine used to attack other machines. 

Please keep in mind the following:
1. Pentesting any target that is not deployed by you on TryHackMe is prohibited.
2. Once this machine is terminated, all data will be lost.
3. This machine expires. Check TryHackMe to ensure you still have time left.

Usage Instructions:
1. Tools are located in /root/Desktop/Tools & /opt/
2. Webshells are located in /usr/share/webshells
3. Wordlists are located in /usr/share/wordlists
4. To use Empire & Starkiller, read the following file: /root/Instructions/empire-starkiller.txt

## Offensive cyber security

This area involves attacking different applications and technologies to discover vulnerabilities.

This career is for you if:
- you enjoy understanding how things work
- you are analytical
- you like thinking out of the box

The most common offensive security job role is a **penetration tester**. A penetration tester is an individual that is legally employed by an organisation to find vulnerabilities in their products. A penetration tester usually requires a broad range of knowledge including:

- web application security
- network security
- use of programming languages to write various scripts

More recently, cloud security has also been gaining popularity as various organisations are now shifting their infrastructure to cloud providers such as AWS and Azure.

It's also possible to have a speciality in one of these topics, however a broad knowledge is the best way to start out.

## Defensive cyber security

While Offensive Security involves actively finding vulnerabilities and misconfigurations within technologies, Defensive Security involves detecting and stopping these attacks.

This career track is for you if:
- you are analytical
- you enjoy problem solving

One of the careers under this track is a **Security Analyst**. This is an individual in an organisation who's job is to monitor various systems in the organisation and detect whether any of these systems are being attacked. To do this, you need to understand how underlying technologies work and then understand what attacks against these technologies look like. 

While a Security Analyst deals with detecting attacks, an **Incident Responder** is usually brought in once an attack has already occurred. Their main responsibilities include understanding what actions an attacker has taken in the organisation and what the impact of their actions will be. Incident Responders also need to know how underlying technologies work and what potential attacks could be carried out against a system. They then analyse trace evidence left by an attacker.

While this is a very specialist role, **malware analysis** is quite common when detecting and responding to attacks. Malicious actors would use malicious pieces of software in any stage of their attack cycle from gaining access to a system to maintaining persistence. If you can understand what exactly this malware is doing, you can prevent further abuse and also identify the malicious action. 

## Research

Without a doubt, **the ability to research effectively** is the most important quality for a hacker to have. By its very nature, hacking requires a vast knowledge base -- because how are you supposed to break into something if you don't know how it works? The thing is: no one knows everything. Everyone (professional or amateur, experienced or totally new to the subject) will encounter problems which they don't automatically know how to solve. This is where research comes in, as, in the real world, you can't ever expect to simply be handed the answers to your questions.

As your experience level increases, you will find that the things you're researching scale in their difficulty accordingly; however, in the field of information security, there will never come a point where you don't need to look things up.

Notice the methodology here. We started with nothing, but gradually built up a picture of what we needed to do. We had a question (How can I extract data from this image). We searched for an answer to that question, then continued to query each of the answers we were given until we had a full understanding of the topic. This is a really good way to conduct research: Start with a question; get an initial understanding of the topic; then look into more advanced aspects as needed.

## Vulnerability searching

Often in hacking you'll come across software that might be open to exploitation. For example, Content Management Systems (such as Wordpress, FuelCMS, Ghost, etc) are frequently used to make setting up a website easier, and many of these are vulnerable to various attacks. So where would we look if we wanted to exploit specific software?

The answer to that question lies in websites such as:
- ExploitDB
    - ExploitDB tends to be very useful for hackers, as it often actually contains exploits that can be downloaded and used straight out of the box. It tends to be one of the first stops when you encounter software in a CTF or pentest.
- NVD
    - NVD keeps track of CVEs (Common Vulnerabilities and Exposures) -- whether or not there is an exploit publicly available -- so it's a really good place to look if you're researching vulnerabilities in a specific piece of software. CVEs take the form: CVE-YEAR-IDNUMBER
- CVE Mitre

If you're inclined towards the CLI on Linux, Kali comes pre-installed with a tool called "searchsploit" which allows you to search ExploitDB from your own machine. This is offline, and works using a downloaded version of the database, meaning that you already have all of the exploits already on your Kali Linux!

Linux (usually Kali Linux) is without a doubt the most ubiquitous operating system used in hacking, so it pays to be familiar with it!

Any information can potentially be useful -- so feel free to use blogs, wikipedia, or anything else that contains what you're looking for! Blogs especially can often be very valuable for learning when it comes to information security, as many security researchers keep a blog.