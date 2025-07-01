# 🧠 Memory Forensics Investigation using Volatility

## 🔍 Project Overview

This project showcases a complete **memory forensics investigation** conducted on a compromised Windows machine using the **Volatility Framework**. Memory forensics plays a vital role in modern incident response, especially in identifying fileless malware, privilege escalation attempts, reverse shells, and persistence mechanisms that reside entirely in RAM.

The challenge was conducted via [TryHackMe's Memory Forensics Room](https://tryhackme.com/room/memoryforensics) and simulated a real-world memory analysis scenario involving malware, suspicious processes, and network activity.

---

## 🎯 Objectives

- Extract forensic artifacts from a Windows memory dump
- Identify suspicious or malicious processes
- Analyze in-memory indicators of compromise (IoCs)
- Reconstruct attacker behavior from memory traces
- Practice using Volatility in an incident response workflow

---

## 🛠️ Tools & Setup

| Tool             | Use Case                                 |
|------------------|-------------------------------------------|
| **Volatility 2** | Memory dump analysis                      |
| **Windows PowerShell** | Command line operations & file prep       |
| **Kali Linux**   | Support for analysis, SSH, and file transfer |
| **TryHackMe VM** | Source of memory dump (attacked Windows machine) |

---

## 🧠 Step-by-Step Analysis

---

### 📁 Step 1: Identify the Memory Image Profile

**Command:**
```bash
volatility -f memory.vmem imageinfo
