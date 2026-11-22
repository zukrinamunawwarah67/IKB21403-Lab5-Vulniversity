IKB21403 – Vulnerability Analysis

Lab 5: TryHackMe – Vulniversity

Student: Siti Zukrina Munawwarah Binti Zul Azri
Course: Bachelor of Information Technology (Hons) in Computer System Security
Subject: IKB21403 – Vulnerability Analysis
Lab: Lab 5 – TryHackMe Vulniversity

⸻

1. Introduction

This lab was carried out using the Vulniversity room on TryHackMe. The purpose of this exercise was to understand the basic process of vulnerability assessment and web application testing.

Throughout this lab, I used several tools to investigate the target machine, identify open ports and services, discover hidden directories and examine the file upload functionality.

2. Target Information

Item	Details
Platform	TryHackMe
Room	Vulniversity
Target IP	10.48.149.40
Attacker environment	TryHackMe AttackBox
Attacker IP	10.48.115.136
Operating System	Ubuntu (identified through scanning)
Web server	Apache HTTP Server
Web server port	3333

Note: The IP addresses above were the addresses assigned during my lab session.

3. Methodology and Tools Used

The following tools were used during the exercise:

* Nmap: Used to scan the target machine and identify open ports and running services.
* Gobuster: Used to discover directories and hidden paths on the web server.
* Burp Suite: Used to inspect HTTP requests and understand how the website handled file uploads.
* Netcat: Used to listen for an incoming connection during the reverse-shell exercise.
* PHP Reverse Shell: Used as the payload provided in the TryHackMe exercise.

4. Step-by-Step Process

Step 1: Deploying the Target Machine

I started by deploying the target machine in TryHackMe and connecting to the AttackBox. I used the ping command to check whether the target machine was reachable.

Step 2: Network Scanning Using Nmap

I performed a service version scan using Nmap to identify open ports and services running on the target.

Command used:

nmap -sV 10.48.149.40

The scan identified six open TCP ports: 21, 22, 139, 445, 3128 and 3333. The web server was running Apache on port 3333.

Step 3: Directory Enumeration Using Gobuster

I used Gobuster to discover directories available on the web server.

Command used:

gobuster dir -u http://10.48.149.40:3333 -w /usr/share/wordlists/dirbuster/directory-list-1.0.txt

The scan discovered several directories, including /images, /css, /js and /internal. I focused on the /internal/ directory because it contained a file upload page.

Step 4: Investigating the Upload Page

I accessed the upload page under the /internal/ directory and examined its functionality. This stage helped me understand how file uploads could potentially introduce security issues when file validation is not properly implemented.

Step 5: Using Burp Suite

I explored Burp Suite Community Edition to understand how HTTP requests could be intercepted and inspected during web application testing.

I examined the request information and learned how the browser communicates with the web server when submitting data.

Step 6: Identifying the Accepted File Extension

During the exercise, I identified .phtml as the accepted file extension. This was relevant because the extension can be associated with PHP processing, depending on the server configuration.

Step 7: Preparing the PHP Reverse Shell

I downloaded the PHP reverse-shell file provided in the exercise and reviewed the instructions for configuring it. I also prepared Netcat to listen for an incoming connection on port 1234.

This stage helped me understand the basic concept of a reverse shell and how a target machine can initiate a connection back to an attacker machine.

5. Findings

Based on the activities performed, I identified the following findings:

* The target machine was running Ubuntu.
* Six open TCP ports were identified during the Nmap scan.
* Apache HTTP Server was running on port 3333.
* Gobuster discovered the /internal/ directory.
* The directory contained a file upload page.
* Burp Suite was used to inspect HTTP requests.
* The .phtml extension was identified during the upload exercise.
* The lab introduced the preparation of a PHP reverse shell.

6. Screenshots and Evidence

Screenshots taken during the practical exercise are included in the Screenshots folder.

They provide evidence of the machine deployment, network scanning, directory enumeration, upload page investigation, Burp Suite configuration and reverse-shell preparation.

7. User Flag

The user flag is an important part of the practical exercise. It should be included here after it has been successfully retrieved from the target machine.

User flag: [Insert the actual user flag here]

Webserver username: [Insert the verified username here]

8. Conclusion

Overall, this lab gave me practical experience in performing basic vulnerability assessment using TryHackMe. I learned how to identify open ports and services using Nmap, discover directories using Gobuster and inspect HTTP requests using Burp Suite.

I also gained a better understanding of file upload security and the basic concept of a reverse shell. The exercise helped me become more familiar with the tools used in penetration testing and understand why reconnaissance is an important part of security testing.

⸻

Reference: TryHackMe – Vulniversity
https://tryhackme.com/room/vulniversity
