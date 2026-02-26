# Task 1 — Basic Network Scanning with Nmap

This task demonstrates a foundational cybersecurity skill: performing a network scan to identify open ports and running services on a target system. For this assignment, the target was the local machine (`127.0.0.1`), which satisfies the internship requirement to scan a local host or VM.

The scan was performed using **Nmap** and **Zenmap (GUI)** with the **Intense Scan** profile, which includes service detection, OS detection, script scanning, and traceroute.

---

## 🔧 Tools Used
- **Nmap 7.88**
- **Zenmap (Nmap GUI)**
- Localhost target (`127.0.0.1`)

---

## 📌 Scan Command Executed

```
nmap -T4 -A -v 127.0.0.1
```

This command performs:
- Aggressive scan (`-A`)
- Version detection (`-sV`)
- OS detection
- Script scanning
- Traceroute
- Increased speed (`-T4`)
- Verbose output (`-v`)

---

## 📊 Summary of Findings

The scan identified **5 open ports** on the local machine:

| Port      | State | Service        | Version                                      |
|-----------|--------|----------------|--------------------------------------------------|
| **135/tcp** | open  | msrpc          | Microsoft Windows RPC            |
| **445/tcp** | open  | microsoft-ds   | SMB file sharing service                         |
| **1042/tcp** | open  | afrog | Service guess                    |
| **1043/tcp** | open  | ssl/boinc | Service guess                   |
| **5357/tcp** | open | http           | Microsoft HTTPAPI httpd 2.0 (SSDP/UPnP)  |

These results indicate that the system is running standard Windows services, along with VMware‑related services if virtualization tools are installed.

---

## 📁 Files Included in This Task

```
Task1-Nmap/
├── nmap_scan_results.txt      # Full text output from the scan
├── screenshots/               # Zenmap screenshots
│     ├── Nmap Screenshot 2026-02-25.1.png
│     ├── Nmap Screenshot 2026-02-25.2.png
│     ├── Nmap Screenshot 2026-02-25.3.png
|     └── Nmap Screenshot 2026-02-25.4.png
└── README.md                  # This file
```


---

## 🖼️ Screenshots

Screenshots of the Zenmap output are included in the `screenshots/` folder as required by the internship instructions.

---

## 📘 Interpretation

- **RPC (135)** and **SMB (445)** are common Windows services used for remote procedure calls and file sharing.
- **VMware ports (1042, 1043)** appear when VMware Workstation or similar virtualization tools are installed.
- **Port 5357 (HTTP)** is used by Windows for device discovery and web services.

These findings are normal for a Windows host and demonstrate that the scan successfully identified active services.

---

## ✅ Internship Requirements Covered

This task fulfills the following required components:

- ✔ Perform a network scan  
- ✔ Identify open ports and services  
- ✔ Document findings  
- ✔ Provide screenshots  
- ✔ Include scan output file  
- ✔ Create a task‑specific README  

