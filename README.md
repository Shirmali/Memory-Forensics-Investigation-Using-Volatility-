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
# 🧠 Memory Forensics Investigation Using Volatility 3

This project demonstrates the installation and usage of [Volatility 3](https://github.com/volatilityfoundation/volatility3) on Windows for memory forensics analysis. I analyzed a memory dump (`snapshot2.vmem`) using Volatility 3 plugins to extract forensic artifacts like running processes, loaded DLLs, and command-line history.

---

## 🛠️ Volatility 3 Installation (Windows)

### 1. Download Volatility 3
- Visit the [official GitHub repo](https://github.com/volatilityfoundation/volatility3)
- Click **Code > Download ZIP**
- Extract the contents to: Volatility3
- C:\Users\Administrator\Downloads\volatility3

---

---

### 2. Install Python 3 (if not already installed)
- Download the latest Python 3 from [python.org](https://www.python.org/)
- During installation, ensure you check:
✅ **Add Python to PATH**

To verify:
<pre> ```powershell python --version ``` </pre>


---
3. Install Required Dependencies
Navigate to the volatility3 folder and run:

<pre> ```powershell cd C:\Users\Administrator\Downloads\volatility3\volatility3-develop pip install -r requirements.txt ``` </pre>

---
✅ My Preferred Setup: Running Volatility as vol
To simplify usage, I created a global shortcut to run vol.py from any PowerShell window using just vol.

🔧 Create a Shortcut (vol.bat)
1. Create a folder:

<pre> ```makefile C:\Tools\ ``` </pre>

---

2. Inside it, create a file named vol.bat with the following contents:

<pre> ``` bat @echo off
python "C:\Users\Administrator\Downloads\volatility3\volatility3-develop\vol.py" %* ``` </pre>
                                                                                      

---

3. Add C:\Tools\ to your System PATH:

Open System Properties > Environment Variables

Under System Variables, edit Path and add:

<pre> ```makefile C:\Tools\ ``` </pre>

---

4. Restart PowerShell and test:

<pre> ```powershell vol -h ``` </pre>
### 📁 Step 1: Identify the Memory Image Profile

**Command:**
```bash
volatility -f memory.vmem imageinfo
