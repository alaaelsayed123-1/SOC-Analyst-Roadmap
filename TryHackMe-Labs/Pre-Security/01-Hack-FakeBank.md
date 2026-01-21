# TryHackMe – Hack FakeBank

## Lab Information
- Platform: TryHackMe  
- Learning Path: Pre-Security  
- Room Name: Offensive Security Intro – Hack FakeBank  
- Difficulty Level: Beginner  
- Completion Status: Completed (100%)

This lab introduces basic offensive security concepts by demonstrating how attackers can discover and abuse hidden web application functionality.

---

## Objective
The main objective of this lab is to discover hidden or unlinked web pages within the FakeBank application and understand how improper access control can allow unauthorized users to perform sensitive actions.

From a defensive (SOC) perspective, the goal is to understand how such attacks work in order to detect and prevent them.

---

## Environment Details
- Target Web Application: http://fakebank.thm  
- Attack Technique: Directory Brute-Forcing  
- Tool Used: dirb  
- Attacker Access Level: Unauthenticated user  

The lab simulates a real-world scenario where an attacker interacts with a public-facing web application without valid credentials.

---

## Tool Explanation: dirb
**dirb** is a web content discovery tool used to brute-force directories and files on a web server.

It works by:
- Taking a predefined wordlist of common directory and file names
- Sending HTTP requests to the target URL
- Analyzing server responses to determine which pages exist

dirb does **not** bypass authentication.  
Instead, it reveals pages that are:
- Hidden
- Not linked in the website navigation
- Forgotten by developers
- Improperly protected

---

## Command Executed
```bash
dirb http://fakebank.thm

