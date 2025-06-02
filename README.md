# 🛡️ Metasploitable2 on Mac M4: Your Legacy Pentest Lab Rebuilt for Apple Silicon (How To)
**By Carla Vieira — May 2025**  
> Traditional virtualization broke on Apple Silicon — but legacy vulnerabilities didn’t disappear. This guide rebuilds a Metasploitable2 environment on Mac M4 using UTM, enabling safe, hands-on testing of real-world exploits on modern hardware.

---

## ⚠️ Why This Tutorial Matters

Setting up proper penetration testing infrastructure is non-negotiable for cybersecurity professionals. But with the shift to Apple’s M1–M4 chips, popular tools like **VirtualBox** and **VMware** lost compatibility with x86-based test environments.

**That meant no XP, no Metasploitable2 — and no legacy exploit simulation.**  
This project solves that by using **UTM + QEMU** to restore full legacy lab functionality, directly on Apple Silicon.

---

## 🚀 TL;DR – What You’ll Have by the End

✅ Fully functional **Metasploitable2** lab running on Mac M4  
✅ Understanding of **UTM virtualization** for cybersecurity testing  
✅ **Network configuration** for safe exploit simulation  
✅ **Connection validation** between attacker (Kali) and target (Metasploitable2)

---

## 💡 Why Metasploitable2?

Metasploitable2, generously maintained by [Rapid7](https://sourceforge.net/projects/metasploitable/), is an intentionally vulnerable Linux distro for ethical hacking and security research.

### Key Features:
- Multiple exploitable services (FTP, SSH, HTTP, etc.)
- Realistic misconfigurations mimicking real-world targets
- Safe, isolated penetration testing environment
- Perfect for practicing **MS08-067**, **SMBv1**, **Heartbleed**, and more

---

## 🧰 What You’ll Need

### System Requirements:
- Mac with **Apple M1, M2, M3, or M4 chip**
- **4GB+ RAM**, **10GB+ free disk**
- **UTM** installed from [https://mac.getutm.app](https://mac.getutm.app)

---

## 🛠️ Setup Instructions

### 1. Install UTM

- Visit [UTM](https://mac.getutm.app/)
- Download and install the latest version for macOS
- (Optional but recommended: Purchase to support the project and unlock full features)

---

### 2. Download Metasploitable2

- Get it from SourceForge: [https://sourceforge.net/projects/metasploitable/](https://sourceforge.net/projects/metasploitable/)
- Extract the `.zip` and locate the `.vmdk` file

---

### 3. Create a New VM in UTM

- Open UTM → click “+” → select **Emulate** (not Virtualize)  
- Choose **Other** OS  
- Set Boot Device to “None”  
- Continue until you see the **Summary** screen  
- Click **“Open VM Settings”**

---

### 4. Configure the VM

#### General
- Name: `Metasploitable2-Testing`

#### QEMU Settings
- Uncheck **UEFI Boot**

#### Drives
- Delete default IDE drive  
- Click **New Drive → Import**, then select the `.vmdk` file

#### Hardware
- RAM: 1GB  
- CPU: Default

---

### 5. First Boot

- Start the VM  
- Login with:
  - **Username**: `msfadmin`  
  - **Password**: `msfadmin`

---

### 6. Network Configuration & Validation

- Find the VM’s IP address via `ifconfig` or `ip a`
- From your host Mac or your Kali VM, ping the Metasploitable2 VM to validate the connection. Run:

```bash
ping <Metasploitable2_IP>
```

![Alt text](screenshots/BLOG2_8.jpg)




