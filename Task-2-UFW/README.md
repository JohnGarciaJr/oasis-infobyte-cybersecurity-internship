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
```

### 2. Enable the Firewall
```bash
sudo ufw enable
```

### 3. Allow SSH (Port 22)
```bash
sudo ufw allow ssh
```

### 4. Deny HTTP (Port 80)
```bash
sudo ufw deny 80/tcp
```

### 5. Check Firewall Status
```bash
sudo ufw status numbered
```

---

## 📂 Files Included

### **ufw_configuration.sh**
A shell script that installs and configures UFW automatically.

### **screenshots/**
Contains screenshots showing:
- UFW enabled  
- Allowed and denied rules  
- Final firewall status  

---

## 🎥 Demo Video - Posted on LinkedIn
A short walkthrough demonstrating:
- Running the script  
- Verifying UFW rules  
- Explaining the configuration  

---

## ✅ Internship Requirement Status
This task is **complete** and includes:
- `ufw_configuration.sh`  
- Screenshot of active UFW rules  
- README.md  
- Demo video - Posted on LinkedIn
