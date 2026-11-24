

# IKB21403 – Vulnerability Analysis
## Lab 5: TryHackMe – Vulniversity

**Student Name:** Siti Zukrina Munawwarah binti Zul Azri

**Student ID:** 52215125652

**Course:** Bachelor in Cybersecurity Technology (BCS)

**Class:** L01 - B04

**Subject:** IKB21403 – Vulnerability Analysis

**Platform:** TryHackMe

---

## 1. Introduction

This lab was carried out using the Vulniversity room on TryHackMe. The main purpose of this exercise was to practise a basic vulnerability assessment and web application testing process.

During this practical, I used different tools to identify open ports and services, discover hidden directories, investigate a file upload feature and perform a reverse-shell exercise.

## 2. Target Information and Lab Environment

| Item | Details |
|---|---|
| Platform | TryHackMe |
| Room | Vulniversity |
| Attacker IP Address | 10.48.122.200 |
| Target IP Address | 10.48.174.247 |
| Attacker Environment | TryHackMe AttackBox |
| Operating System | Ubuntu |
| Web Server | Apache HTTP Server 2.4.41 |
| Web Server Port | 3333 |

*Note: The IP addresses above were taken from my later practical session. TryHackMe assigns different private IP addresses whenever the machines are redeployed.*

## 3. Methodology and Tools Used

The following tools were used during this practical:

- **Nmap:** Used to scan the target machine and identify open ports, running services and their versions.
- **Gobuster:** Used to discover hidden directories and paths on the web server.
- **Burp Suite Community Edition:** Used to examine proxy settings and understand how HTTP requests can be intercepted and inspected.
- **Netcat:** Used to listen for an incoming connection during the reverse-shell exercise.
- **PHP Reverse Shell:** The PHP reverse-shell file supplied by the TryHackMe exercise was used during the controlled lab.

## 4. Step-by-Step Process

### Step 1: Deploy the Target Machine and Check Connectivity

I started by deploying the Vulniversity machine on TryHackMe and connecting to the AttackBox. I checked that the target machine was reachable before continuing with the practical.

The IP addresses shown in my later session were:

- Attacker IP: `10.48.122.200`
- Target IP: `10.48.174.247`

### Step 2: Network Scanning Using Nmap

I performed a service-version scan using Nmap to identify the open ports and services running on the target machine.

**Command used:**

```bash
nmap -sV 10.48.174.247
```

The scan identified six open TCP ports:

| Port | Service / Version |
|---|---|
| 21 | FTP – vsftpd 3.0.5 |
| 22 | SSH – OpenSSH 8.2p1 Ubuntu |
| 139 | NetBIOS-SSN – Samba smbd 4.6.2 |
| 445 | NetBIOS-SSN – Samba smbd 4.6.2 |
| 3128 | HTTP Proxy – Squid 4.10 |
| 3333 | HTTP – Apache HTTP Server 2.4.41 |

### Step 3: Directory Enumeration Using Gobuster

After identifying the web service on port 3333, I used Gobuster to search for hidden directories and files on the web server.

**Command used:**

```bash
gobuster dir -u http://10.48.174.247:3333 -w /usr/share/wordlists/dirb/common.txt
```

During the enumeration, I discovered several directories, including:

- `/css`
- `/fonts`
- `/images`
- `/internal`
- `/js`
- `/server-status`

The `/internal/` directory was important because it contained the file upload page used in the next stage.

### Step 4: Investigating the File Upload Page

I accessed the `/internal/` directory through the browser and found a file upload form.

I examined the page and carried out the file upload exercise provided by TryHackMe. After selecting and submitting the file, the page displayed a success message.

This helped me understand how file upload functionality can introduce security risks if uploaded files are not properly validated.

### Step 5: Inspecting HTTP Traffic Using Burp Suite

I opened Burp Suite Community Edition and checked the proxy settings.

The proxy listener was configured on:

`127.0.0.1:8080`

This helped me understand how Burp Suite can be used to intercept and inspect HTTP requests during web application testing.

### Step 6: Identifying the Accepted File Extension

During the exercise, I identified `.phtml` as the accepted file extension for the next stage.

This was important because PHP-related file extensions may allow server-side code execution when the web server is configured to process them.

### Step 7: Preparing the PHP Reverse Shell and Starting Netcat

I opened the PHP reverse-shell file supplied by the TryHackMe room and checked the callback settings.

The callback IP address was set to the AttackBox's `tun0` address, and the file was renamed to:

`php-reverse-shell.phtml`

I then started a Netcat listener on port 1234.

**Command used:**

```bash
nc -lvnp 1234
```

### Step 8: Confirming the Reverse-Shell Connection

After uploading the prepared file and starting the listener, Netcat received an incoming connection from the target machine.

I used the following command to identify the current user:

```bash
whoami
```

The output returned:

`www-data`

This confirmed that the reverse-shell connection was successfully established. However, the shell was running as `www-data`, not root.

I also used basic navigation and listing commands to inspect the target machine. The `/home` directory contained a user folder named `bill`.

### Step 9: Locating and Reading the User Flag

I navigated to `/home/bill` and located the `user.txt` file.

I used the `cat` command to display its contents.

**Command used:**

```bash
cat /home/bill/user.txt
```

**User Flag:**

```text
8bd7992fbe8a6ad22a63361004cfcedb
```

## 5. Findings

Based on the activities performed, I identified the following findings:

- The target machine was reachable from the TryHackMe AttackBox.
- Six open TCP ports were identified using Nmap.
- The target was running FTP, SSH, Samba, Squid Proxy and Apache HTTP services.
- Apache HTTP Server 2.4.41 was accessible on port 3333.
- Gobuster discovered the `/internal/` directory and other web paths.
- A file upload form was available under the `/internal/` directory.
- The `.phtml` extension was accepted for the next stage.
- Burp Suite was used to examine the proxy configuration.
- Netcat successfully received a reverse-shell connection.
- The shell was running under the `www-data` account rather than root.
- The `user.txt` file was located in `/home/bill` and the user flag was successfully retrieved.

## 6. Screenshots and Evidence

Screenshots from the practical exercise are included in the report and supporting project files.

The evidence covers the following activities:

1. Target machine deployment and connectivity.
2. Nmap service scanning results.
3. Gobuster directory enumeration.
4. Investigation of the file upload page.
5. Burp Suite proxy configuration.
6. Identification of the accepted `.phtml` extension.
7. PHP reverse-shell preparation.
8. Successful Netcat connection and user identification.
9. Locating and retrieving the user flag.
10. TryHackMe room completion.

These screenshots provide evidence of the practical activities performed throughout the exercise.

## 7. User Flag

The user flag obtained during the practical exercise was:

**Webserver username:** `bill`

**Shell user:** `www-data`

**User flag:**

`8bd7992fbe8a6ad22a63361004cfcedb`

## 8. Completion Status

I successfully completed the TryHackMe Vulniversity room.

The final progress screenshot showed:

- Room completion: 100%
- Completed tasks: 5
- Points earned: 104

This practical allowed me to apply the techniques learned throughout the exercise, from reconnaissance and directory enumeration to file upload investigation and the reverse-shell activity.

## 9. Conclusion

Overall, this lab gave me useful hands-on experience in performing a basic vulnerability assessment using TryHackMe.

I learned how to identify open ports and services using Nmap, discover hidden directories using Gobuster and examine HTTP proxy settings using Burp Suite.

I also gained a better understanding of file upload security and the basic concept of a reverse shell. Through this exercise, I was able to establish a reverse-shell connection, identify the shell user as `www-data` and retrieve the user flag from `/home/bill/user.txt`.

This practical helped me understand why reconnaissance, proper evidence collection and checking the actual access level are important during security testing.

## References

- TryHackMe. (n.d.). *Vulniversity*. https://tryhackme.com/room/vulniversity
- GitHub Repository: IKB21403-Lab5-Vulniversity

---

**Note:** This lab was initially carried out on an earlier date, during which the target and attacker machines were assigned different IP addresses. After pausing the practical session, I accidentally terminated the lab machine. When I redeployed the room to continue and capture the remaining screenshots, new IP addresses were assigned. Therefore, some screenshots may show different IP addresses. All screenshots are taken from my own practical work on the TryHackMe Vulniversity room.
