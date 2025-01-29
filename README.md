# 🚀 Jenkins Installation Guide

A complete guide to setting up **Jenkins** on **Ubuntu, CentOS, macOS, and Windows**.

## 📌 Table of Contents

- [Prerequisites](#prerequisites)
- [Installation](#installation)
  - [Ubuntu/Debian](#ubuntu-debian)
  - [CentOS/RHEL](#centos-rhel)
  - [macOS](#macos)
  - [Windows (Chocolatey)](#windows-chocolatey)
  - [Installing Chocolatey](#installing-chocolatey)
- [Post-Installation](#post-installation)
- [Troubleshooting](#troubleshooting)
- [References](#references)

## ✅ Prerequisites

- 🔑 **Admin/Sudo Access**
- 🌐 **Internet Connectivity**
- 🖥️ **Terminal Access**

## 🚀 Installation

### 🐧 Ubuntu/Debian

```bash
# Add Jenkins repo key
curl -fsSL https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key | sudo tee /usr/share/keyrings/jenkins-keyring.asc > /dev/null

# Add Jenkins repository
echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \  
  https://pkg.jenkins.io/debian-stable binary/ | sudo tee \  
  /etc/apt/sources.list.d/jenkins.list > /dev/null

# Install and Start Jenkins
sudo apt update
sudo apt install jenkins
sudo systemctl start jenkins
sudo systemctl enable jenkins
```

### 📀 CentOS/RHEL

```bash
# Add repo and key
sudo wget -O /etc/yum.repos.d/jenkins.repo https://pkg.jenkins.io/redhat-stable/jenkins.repo
sudo rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io-2023.key

# Install Jenkins
sudo dnf upgrade
sudo dnf install jenkins

# Start Jenkins
sudo systemctl start jenkins
sudo systemctl enable jenkins
```

### 🍏 macOS (Homebrew)

```bash
brew install jenkins
brew services start jenkins
```

### 🖥️ Windows (Chocolatey)

```powershell
# Install Jenkins using Chocolatey
choco install jenkins -y

# Start Jenkins service
Start-Service jenkins

# Enable Jenkins to start on boot
Set-Service -Name jenkins -StartupType Automatic
```

Once installed, access Jenkins at **[http://localhost:8080](http://localhost:8080)** and retrieve the initial admin password:

```powershell
Get-Content "C:\\ProgramData\\Jenkins\\.jenkins\\secrets\\initialAdminPassword"
```

Follow the on-screen setup wizard to complete the installation.

### 🏗 Installing Chocolatey

Chocolatey is required to install Jenkins on Windows. If you don’t have it installed, follow these steps:

1. Open **PowerShell as Administrator**
2. Run the following command:

```powershell
Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))
```

3. Close and reopen PowerShell
4. Verify installation with:

```powershell
choco -v
```

## 🔎 Post-Installation

- Open Jenkins at **[http://localhost:8080](http://localhost:8080)**
- Retrieve admin password:
  ```bash
  sudo cat /var/lib/jenkins/secrets/initialAdminPassword
  ```
- Complete the setup wizard in the browser

## 🛠 Troubleshooting

- **Port Conflict?**\
  Change port in `/etc/default/jenkins` (Linux) or `/usr/local/opt/jenkins/homebrew.mxcl.jenkins.plist` (macOS)

- **Jenkins Not Running?**\
  Check status:

  ```bash
  systemctl status jenkins  # Linux
  brew services list        # macOS
  ```

## 📚 References

- [Jenkins Official Docs](https://www.jenkins.io/doc/)
- [Chocolatey Official Docs](https://docs.chocolatey.org/en-us/)

