
# IKB21403 – Vulnerability Analysis
## Lab 5: TryHackMe – Vulniversity

**Student Name:** Siti Zukrina Munawwarah binti Zul Azri  
**Student ID:** 52215125652
**Course:** Bachelor in Cybersecurity Technology (BCS)

**Subject:** IKB21403 – Vulnerability Analysis  

**Platform:** TryHackMe

---

## 1. Introduction

This lab was carried out using the Vulniversity room on TryHackMe. The main purpose of this exercise was to learn how to perform basic vulnerability assessment and web application testing.

During this lab, I used different tools to investigate the target machine, identify open ports and services, discover hidden directories and examine the file upload functionality.

## 2. Target Information

| Item | Details |
|---|---|
| Platform | TryHackMe |
| Room | Vulniversity |
| Target IP Address | 10.48.149.40 |
| Attacker IP Address | 10.48.115.136 |
| Attacker Environment | TryHackMe AttackBox |
| Operating System | Ubuntu |
| Web Server | Apache HTTP Server |
| Web Server Port | 3333 |

*Note: The IP addresses shown above were assigned during my lab session.*

## 3. Methodology and Tools Used

The following tools were used during the practical exercise:

- **Nmap:** Used to scan the target machine and identify open ports and running services.
- **Gobuster:** Used to discover directories and hidden paths on the web server.
- **Burp Suite:** Used to inspect HTTP requests and understand the website's file upload functionality.
- **Netcat:** Used to listen for an incoming connection during the reverse-shell exercise.
- **PHP Reverse Shell:** Used as part of the reverse-shell exercise provided by TryHackMe.

## 4. Step-by-Step Process

### Step 1: Deploying the Target Machine

I started by deploying the Vulniversity machine on TryHackMe and connecting to the AttackBox. I used the ping command to check whether the target machine was reachable.

### Step 2: Network Scanning Using Nmap

I performed a service version scan using Nmap to identify the open ports and services running on the target machine.

**Command used:**

```bash
nmap -sV 10.48.149.40
```

The scan identified six open TCP ports:

| Port | Service |
|---|---|
| 21 | FTP |
| 22 | SSH |
| 139 | NetBIOS-SSN |
| 445 | NetBIOS-SSN |
| 3128 | Squid HTTP Proxy |
| 3333 | HTTP |

The scan also identified Squid version 4.10 and Apache HTTP Server version 2.4.41.

### Step 3: Directory Enumeration Using Gobuster

I used Gobuster to search for hidden directories and files on the web server.

The purpose of this step was to identify directories that were not directly visible from the main website.

During the enumeration, I identified the `/internal/` directory, which contained a file upload page.

### Step 4: Investigating the Upload Page

I accessed the upload page under the `/internal/` directory and examined its functionality.

This step helped me understand how file uploads could potentially introduce security risks when the website does not properly validate uploaded files.

### Step 5: Using Burp Suite

I explored Burp Suite Community Edition to understand how HTTP requests could be intercepted and inspected during web application testing.

I also examined the proxy configuration and request interception settings.

### Step 6: Identifying the Accepted File Extension

During the exercise, I identified `.phtml` as the accepted file extension.

This was important because PHP-related file extensions can allow server-side code execution when the web server is configured to process them.

### Step 7: Preparing the PHP Reverse Shell

I downloaded the PHP reverse-shell file provided in the exercise and followed the instructions to prepare it.

I also used Netcat to listen for an incoming connection on port 1234.

This activity helped me understand the basic concept of a reverse shell and how a target machine can initiate a connection back to an attacker machine.

## 5. Findings

Based on the activities performed, I identified the following findings:

- The target machine was running Ubuntu.
- Six open TCP ports were identified.
- Apache HTTP Server was running on port 3333.
- Squid HTTP Proxy version 4.10 was identified.
- The `/internal/` directory was discovered.
- A file upload page was available.
- The `.phtml` extension was identified as an accepted extension.
- Burp Suite was used to inspect HTTP requests.
- Netcat was prepared to listen for an incoming connection.

## 6. Screenshots and Evidence

Screenshots from the practical exercise are included in the `Screenshots` folder of this repository.

The screenshots show the different stages of the exercise, including:

1. Target machine deployment.
2. Nmap scanning results.
3. Directory enumeration.
4. File upload page investigation.
5. Burp Suite configuration.
6. File extension identification.
7. PHP reverse-shell preparation.
8. TryHackMe room completion.

These screenshots are included to provide evidence of the practical work performed.

## 7. User Flag

The user flag is one of the requirements of this exercise.

**Webserver username:** [Insert verified username]

**User flag:** [Insert actual user flag]

*Note: The actual values should only be included after successfully retrieving them from the target machine.*

## 8. Conclusion

Overall, this lab gave me practical experience in performing basic vulnerability assessment using TryHackMe.

I learned how to identify open ports and services using Nmap, discover hidden directories using Gobuster and inspect HTTP requests using Burp Suite.

I also gained a better understanding of file upload security and the basic concept of a reverse shell.

This exercise helped me become more familiar with penetration testing tools and understand why reconnaissance is an important part of vulnerability assessment.

## Reference

TryHackMe – Vulniversity

https://tryhackme.com/room/vulniversity
