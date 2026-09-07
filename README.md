# TRY HACK ME MR ROBOT
# TryHackMe: Mr. Robot

A practical penetration-testing lab completed on TryHackMe.

## 🎯 Objective

The objective of this room was to compromise the target machine, identify vulnerabilities, gain initial access, and ultimately obtain root-level access.

## 🖥️ Lab Information

* **Platform:** TryHackMe
* **Room:** Mr. Robot
* **Difficulty:** Medium
* **Category:** Web Security / Linux / Privilege Escalation
* **Status:** Completed

## 🔎 Methodology

The assessment followed a typical penetration-testing workflow:

1. Reconnaissance
2. Port and service enumeration
3. Web application enumeration
4. Vulnerability identification
5. Initial access
6. Local enumeration
7. Privilege escalation
8. Post-exploitation analysis

## 1. Reconnaissance

Started by identifying the available services on the target.

```bash
nmap -sC -sV <10.48.133.2>
```

The scan revealed several interesting services that required further investigation.

## 2. Web Enumeration

The web server was investigated for:

* Hidden directories
* Interesting files
* Web technologies
* Potentially exposed resources
* Authentication mechanisms

Directory enumeration was performed using appropriate tooling.

## 3. Vulnerability Analysis

The discovered web application was analyzed to understand its attack surface and identify a viable path toward initial access.

## 4. Initial Access

After identifying the relevant vulnerability, I obtained access to the target system.

> Sensitive challenge answers, flags, credentials, and exact exploit payloads are intentionally omitted.

## 5. Local Enumeration

Once access was obtained, I investigated the system to determine:

* Current user privileges
* Running processes
* SUID binaries
* Interesting files
* Configuration weaknesses
* Possible privilege-escalation vectors

Example enumeration:

```bash
whoami
id
sudo -l
find / -perm -4000 -type f 2>/dev/null
```

## 6. Privilege Escalation

The local environment was analyzed for misconfigurations that could allow escalation of privileges.

A notable SUID binary was discovered:

```bash
find / -perm -4000 -type f 2>/dev/null | grep '/bin/'
/usr/local/bin/nmap
```

Because `nmap` was installed with the SUID bit set, it could be used in interactive mode to spawn a root shell:

```bash
/usr/local/bin/nmap --interactive
nmap> !sh
```

This resulted in a privileged shell, allowing root-level access and completion of the challenge.

## 🧠 Key Skills Practiced

* Network enumeration
* Nmap
* Web enumeration
* Directory discovery
* Linux enumeration
* Vulnerability analysis
* Initial access
* Privilege escalation
* Basic post-exploitation
* Penetration-testing methodology




## 📚 What I Learned

This room helped reinforce the importance of:

* Thorough enumeration before exploitation
* Understanding the technologies running on a target
* Thinking systematically rather than relying on a single tool
* Enumerating the Linux environment after obtaining access
* Checking permissions and misconfigurations carefully

## ⚠️ Disclaimer

This repository documents work performed in an authorized TryHackMe training environment.

All testing was conducted against the intentionally vulnerable machine provided by the platform.

## 🏁 Status

**Completed ✅**

TryHackMe: Mr. Robot
https://tryhackme.com/room/mrrobot?utm_campaign=social_share&utm_medium=social&utm_content=share-completed-room&utm_source=copy&sharerId=695682462274dce56cf59248