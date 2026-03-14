# Task 2: Basic Firewall Configuration with UFW

This task demonstrates how to configure a basic firewall using **UFW (Uncomplicated Firewall)** on Ubuntu.  
The goal is to allow secure remote access while blocking unwanted traffic.

---

## 🔧 Objective
- Install and configure UFW  
- Allow SSH traffic  
- Deny HTTP traffic  
- Verify firewall rules  
- Provide documentation, screenshots, and a configuration script

---

## 🛠️ Tools Used
- **UFW (Uncomplicated Firewall)**  
- Ubuntu Linux (VirtualBox VM)

---

## 📌 Steps Performed

### 1. Install UFW
```bash
sudo apt update
sudo apt install ufw -y
