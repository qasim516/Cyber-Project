# Week 1 — Project Proposal and Fundamentals Report

## Project Proposal

**Title:** Security Assessment of Web Applications Using PortSwigger Web Security Academy

**Objective:**
The goal of this project is to understand how common web application vulnerabilities work, find them in a safe and legal environment, and learn how to explain and fix them like a real security analyst would. Since I don't have a laptop capable of running virtual machines, I'm using PortSwigger Web Security Academy as my lab instead of building local VMs. This still lets me follow the same process the internship asks for: scope, find, test, analyze, rate the risk, and report.

**Scope:**
I'll only be testing the lab instances that PortSwigger itself creates for me when I click "Access the lab." These are unique URLs like `xxxx.web-security-academy.net` that only exist for my account and are meant to be tested. I will not test any other website, app, or network — nothing outside these official lab environments.

**Authorization:**
PortSwigger built these labs specifically so students can practice attacking real vulnerabilities without breaking any law. I'm not testing anyone's real system, so there's no authorization needed beyond having an account, which I already set up.

**Tools I'm using:**
Burp Suite Community Edition (to intercept and modify web requests), the browser's own developer tools, and later on, Wireshark and CyberChef for the network and incident-response parts of the project.

**Rough plan:**

- Week 1: Learn the basics, set up Burp Suite, get one lab solved, write this proposal and the fundamentals report.


**Rules I'm following:**
Only test the lab instances given to me. No real personal or private data gets used anywhere in this project. I'll document everything honestly, including anything that doesn't go as planned, rather than hiding mistakes.

## Fundamentals Report

### What is cybersecurity, and why does it matter?

At its core, cybersecurity is about protecting information and systems from people or things that could cause harm — whether that's a hacker trying to steal data, a piece of malware, or even an employee accidentally deleting something important. As more of our lives move online — banking, shopping, even talking to friends — the amount of valuable data sitting on servers keeps growing, and so does the incentive for someone to go after it.

### Threats, vulnerabilities, and risk

These three words get used a lot in security, and it's easy to confuse them. A **threat** is anything that could cause harm — a hacker, a virus, even a natural disaster that takes down a server. A **vulnerability** is a weakness that a threat could take advantage of — like a website that doesn't check user input properly, or an employee using "password123." **Risk** is basically how worried you should actually be about a given vulnerability, and it's usually described as:

**Risk = Likelihood × Impact**

So a vulnerability that's very easy to exploit and would cause massive damage is high risk. A vulnerability that's hard to exploit and wouldn't cause much damage even if someone did is low risk. This is exactly what I saw when doing the SQL injection lab — the vulnerability was easy to find (just add a quote mark to a URL) and the impact was serious (full access to data that should've been hidden), which is why it's rated high severity.

Two related ideas are **defense in depth** (don't rely on just one security measure — use several layers, so if one fails, another catches it) and **least privilege** (give people and programs only the access they actually need, nothing more, so if something does go wrong, the damage is limited).

### Common types of threats

- **Phishing and social engineering** — tricking someone into giving up a password or clicking something harmful, usually through a fake email or message.
- **Malware and ransomware** — malicious software; ransomware specifically locks up your files and demands money to unlock them.
- **Password attacks** — guessing passwords, trying stolen password lists, or exploiting people who reuse the same password everywhere.
- **Denial of Service (DoS)** — flooding a system with traffic so real users can't use it.
- **Man-in-the-Middle (MITM)** — secretly intercepting communication between two parties, like someone eavesdropping on unencrypted Wi-Fi traffic.
- **Insider threats** — harm caused by someone already inside an organization, whether on purpose or by accident.

### The CIA Triad

This is one of the foundational ideas in security — three things you're always trying to protect:

- **Confidentiality** — only the people who should see data can see it. Encryption and access controls are the usual tools here.
- **Integrity** — data stays accurate and isn't tampered with. Things like hashing and backups help confirm nothing's been changed.
- **Availability** — systems and data are there when people actually need them. This is where backups, redundancy, and protection against DoS attacks come in.

A good way to think about it: if an attacker steals your data, that's a confidentiality problem. If they secretly change your data, that's an integrity problem. If they take your system offline, that's an availability problem.

### Authentication, authorization, and accounting

These sound similar but mean different things. **Authentication** is proving who you are — usually a password, but ideally combined with something else like a one-time code (that combination is called **multi-factor authentication**, or MFA). **Authorization** is about what you're allowed to do once you're logged in — a regular user shouldn't have the same access as an admin. **Accounting**, sometimes called auditing, is just keeping a record of who did what and when, which becomes really important if something goes wrong and you need to investigate.

### Networking basics worth knowing

Every device on a network has an IP address (for routing traffic) and a MAC address (a hardware identifier). DNS translates human-friendly names like google.com into IP addresses. DHCP automatically assigns IP addresses to devices when they join a network. TCP is a reliable, connection-based way of sending data; UDP is faster but doesn't guarantee delivery. HTTP sends data in plain, readable text, while HTTPS encrypts it — which is exactly why in the SQL injection lab, if I'd been intercepting someone else's unencrypted HTTP traffic, I could've read it directly.

A few ports worth memorizing because they come up constantly:

- 21 – FTP, 22 – SSH, 23 – Telnet (insecure, should basically never be used today)
- 25 – SMTP (email), 53 – DNS, 80 – HTTP, 443 – HTTPS
- 3306 – MySQL, 3389 – Remote Desktop

### A note on legality

Everything in this project is done inside environments specifically designed for this kind of testing. Testing real systems without written permission is illegal — in Pakistan, this falls under PECA 2016 — so I've made sure every target I touch is one I'm explicitly allowed to test.

### How this connects to what I actually did

The SQL injection lab I completed this week is a good real example of most of these ideas coming together: a vulnerability (unsanitized input) was exploited through a threat (me, acting as an attacker in a controlled setting) to break confidentiality (viewing hidden data), and the fix ties back to good practice (parameterized queries instead of trusting raw input).
