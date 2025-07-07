# Prerequisites & Setup

# VM Setup
# Complete Guide: Installing Oracle VirtualBox and Setting Up Ubuntu VM
# [Tutorial](https://www.youtube.com/watch?v=wX75Z-4MEoM)

## Table of Contents
1. [Prerequisites](#prerequisites)
2. [Downloading Oracle VirtualBox](#downloading-oracle-virtualbox)
3. [Installing VirtualBox](#installing-virtualbox)
4. [Downloading Ubuntu ISO](#downloading-ubuntu-iso)
5. [Creating Ubuntu Virtual Machine](#creating-ubuntu-virtual-machine)
6. [Installing Ubuntu on VM](#installing-ubuntu-on-vm)
7. [Post-Installation Setup](#post-installation-setup)
8. [VirtualBox Guest Additions](#virtualbox-guest-additions)
9. [Troubleshooting](#troubleshooting)
10. [Best Practices](#best-practices)

---

## Prerequisites

### System Requirements

**Minimum Requirements:**
- **RAM**: 4GB (8GB+ recommended)
- **Storage**: 25GB free space (50GB+ recommended)
- **CPU**: 64-bit processor with virtualization support
- **Operating System**: Windows 10/11, macOS 10.15+, or Linux

**Check Virtualization Support:**

#### Windows:
1. Open **Task Manager** → **Performance** tab
2. Click on **CPU**
3. Look for "Virtualization: Enabled"

#### Alternative Method (Windows):
```cmd
# Open Command Prompt as Administrator
systeminfo | find "Hyper-V"
```

#### macOS:
```bash
# Open Terminal
sysctl -a | grep machdep.cpu.features
# Look for VMX (Intel) or SVM (AMD)
```

#### Linux:
```bash
# Check for virtualization support
egrep -c '(vmx|svm)' /proc/cpuinfo
# If output is 1 or higher, virtualization is supported

# Check if VT-x/AMD-V is enabled
lscpu | grep Virtualization
```

---

## Downloading Oracle VirtualBox

### Step 1: Visit Official Website
1. Go to **[https://www.virtualbox.org/](https://www.virtualbox.org/)**
2. Click on **"Downloads"** in the top menu

### Step 2: Choose Your Platform
Select the appropriate version for your operating system:

#### For Windows:
- Click **"Windows hosts"**
- Download the `.exe` file (approximately 104MB)

#### For macOS:
- Click **"macOS hosts"**
- Download the `.dmg` file (approximately 87MB)

#### For Linux:
Choose your distribution:
- **Ubuntu/Debian**: Download `.deb` package
- **Red Hat/CentOS/Fedora**: Download `.rpm` package
- **Generic Linux**: Download `.run` file

### Step 3: Download Extension Pack (Optional but Recommended)
1. Scroll down to **"VirtualBox Extension Pack"**
2. Click **"All supported platforms"**
3. Download the `.vbox-extpack` file

> **Note**: The Extension Pack adds USB 2.0/3.0 support, webcam passthrough, and other advanced features.

---

## Installing VirtualBox

### Windows Installation

#### Step 1: Run the Installer
1. **Right-click** the downloaded `.exe` file
2. Select **"Run as administrator"**
3. Click **"Yes"** when prompted by UAC

#### Step 2: Installation Wizard
1. **Welcome Screen**: Click **"Next"**
2. **Custom Setup**: 
   - Keep default location: `C:\Program Files\Oracle\VirtualBox\`
   - Ensure all features are selected
   - Click **"Next"**
3. **Custom Setup Options**:
   - ✅ Create shortcuts on desktop
   - ✅ Create shortcuts in Quick Launch Bar
   - ✅ Register file associations
   - Click **"Next"**
4. **Network Warning**: 
   - Click **"Yes"** (temporary network disconnection)
5. **Ready to Install**: Click **"Install"**
6. **Installation Progress**: Wait for completion
7. **Completion**: 
   - ✅ Start Oracle VM VirtualBox after installation
   - Click **"Finish"**

### macOS Installation

#### Step 1: Mount the DMG
1. **Double-click** the downloaded `.dmg` file
2. The VirtualBox installer window will open

#### Step 2: Install VirtualBox
1. **Double-click** `VirtualBox.pkg`
2. **Introduction**: Click **"Continue"**
3. **License**: Click **"Continue"** → **"Agree"**
4. **Installation Type**: Click **"Install"**
5. **Authentication**: Enter your admin password
6. **System Extension Blocked** (if prompted):
   - Go to **System Preferences** → **Security & Privacy**
   - Click **"Allow"** next to Oracle software
   - Restart if required

### Linux Installation (Ubuntu/Debian)

#### Method 1: Using Downloaded Package
```bash
# Navigate to download directory
cd ~/Downloads

# Install the package
sudo dpkg -i virtualbox-*.deb

# Fix any dependency issues
sudo apt-get install -f
```

#### Method 2: Using Repository
```bash
# Add Oracle's public key
wget -q https://www.virtualbox.org/download/oracle_vbox_2016.asc -O- | sudo apt-key add -

# Add repository
echo "deb [arch=amd64] https://download.virtualbox.org/virtualbox/debian $(lsb_release -cs) contrib" | sudo tee /etc/apt/sources.list.d/virtualbox.list

# Update package list
sudo apt update

# Install VirtualBox
sudo apt install virtualbox-7.0
```

### Installing Extension Pack

1. **Open VirtualBox**
2. Go to **File** → **Preferences** (or **VirtualBox** → **Preferences** on macOS)
3. Click **"Extensions"** tab
4. Click the **"+"** icon (Add Package)
5. Navigate to downloaded `.vbox-extpack` file
6. Click **"Open"** → **"Install"** → **"I Agree"**
7. Enter admin password when prompted

---

## Downloading Ubuntu ISO

### Step 1: Visit Ubuntu Website
1. Go to **[https://ubuntu.com/download/desktop](https://ubuntu.com/download/desktop)**
2. You'll see the latest LTS (Long Term Support) version

### Step 2: Choose Ubuntu Version

#### Recommended for Beginners:
- **Ubuntu 22.04.3 LTS** (Long Term Support)
- **Size**: ~4.7GB
- **Support**: Until April 2027

#### Alternative Options:
- **Ubuntu 23.10** (Latest version, shorter support)
- **Ubuntu Server** (Command-line only, smaller download)

### Step 3: Download Process
1. Click **"Download Ubuntu [version]"**
2. Optional: Consider donating to support Ubuntu
3. Click **"Download now"** or **"Not now, take me to the download"**
4. Save the `.iso` file to an easily accessible location (e.g., `Downloads` folder)

### Alternative Download Sources (Faster)

#### Official Mirrors:
- **US**: [http://mirror.us.leaseweb.net/ubuntu-releases/](http://mirror.us.leaseweb.net/ubuntu-releases/)
- **Europe**: [http://mirror.eu.leaseweb.net/ubuntu-releases/](http://mirror.eu.leaseweb.net/ubuntu-releases/)
- **Asia**: [http://mirror.asia.leaseweb.net/ubuntu-releases/](http://mirror.asia.leaseweb.net/ubuntu-releases/)

#### Using Torrent (Faster for some):
1. Look for `.torrent` files on the download page
2. Use torrent client like qBittorrent or Transmission

---

## Creating Ubuntu Virtual Machine

### Step 1: Launch VirtualBox
1. **Open VirtualBox**
2. Click **"New"** button (or press `Ctrl+N`)

### Step 2: VM Name and Operating System
1. **Name**: `Ubuntu-Desktop` (or your preferred name)
2. **Machine Folder**: Keep default or choose custom location
3. **Type**: `Linux`
4. **Version**: `Ubuntu (64-bit)`
5. Click **"Next"**

### Step 3: Memory Size (RAM)
**Recommended Settings:**
- **Minimum**: 2048 MB (2GB)
- **Recommended**: 4096 MB (4GB)
- **Optimal**: 8192 MB (8GB) if you have 16GB+ host RAM

**Rule of Thumb**: Don't allocate more than 50% of your total RAM

### Step 4: Hard Disk
1. Select **"Create a virtual hard disk now"**
2. Click **"Create"**

### Step 5: Hard Disk File Type
1. Select **"VDI (VirtualBox Disk Image)"**
2. Click **"Next"**

### Step 6: Storage Type
**Options:**
- **Dynamically allocated**: Grows as needed (recommended for beginners)
- **Fixed size**: Better performance, uses full space immediately

**Recommendation**: Choose **"Dynamically allocated"**

### Step 7: File Location and Size
1. **File location**: Keep default or choose custom path
2. **Size**: 
   - **Minimum**: 25 GB
   - **Recommended**: 50 GB
   - **For development**: 100 GB+
3. Click **"Create"**

---

## Installing Ubuntu on VM

### Step 1: Configure VM Settings

#### Before starting, optimize VM settings:
1. **Right-click** your Ubuntu VM
2. Select **"Settings"**

#### System Settings:
1. **General** → **Advanced**:
   - Shared Clipboard: `Bidirectional`
   - Drag'n'Drop: `Bidirectional`

2. **System** → **Motherboard**:
   - Base Memory: Adjust if needed
   - Boot Order: ✅ Optical, ✅ Hard Disk (uncheck Floppy)
   - ✅ Enable I/O APIC

3. **System** → **Processor**:
   - Processors: 2-4 CPUs (don't exceed green zone)
   - ✅ Enable PAE/NX

4. **Display**:
   - Video Memory: 128 MB (maximum)
   - ✅ Enable 3D Acceleration

### Step 2: Attach Ubuntu ISO
1. In VM Settings, go to **"Storage"**
2. Click on **"Empty"** under Controller: IDE
3. Click the **CD icon** → **"Choose Virtual Optical Disk File"**
4. Navigate to and select your Ubuntu `.iso` file
5. Click **"OK"** to save settings

### Step 3: Start the VM
1. **Select** your Ubuntu VM
2. Click **"Start"** (green arrow)
3. VM window will open and Ubuntu will begin loading

### Step 4: Ubuntu Installation Process

#### Boot Menu:
1. Ubuntu boot screen appears
2. Select **"Try or Install Ubuntu"** (default)
3. Press `Enter` or wait for auto-selection

#### Language Selection:
1. Choose your language (English recommended for tutorials)
2. Click **"Install Ubuntu"**

#### Keyboard Layout:
1. Select your keyboard layout
2. Test typing in the text box
3. Click **"Continue"**

#### Updates and Other Software:
1. **Installation type**:
   - ✅ Normal installation (recommended)
   - ✅ Download updates while installing Ubuntu
   - ✅ Install third-party software for graphics and Wi-Fi hardware
2. Click **"Continue"**

#### Installation Type:
1. Select **"Erase disk and install Ubuntu"**
   - Don't worry - this only affects the virtual disk
2. Click **"Install Now"** → **"Continue"**

#### Time Zone:
1. Click on your location on the map
2. Or manually select your time zone
3. Click **"Continue"**

#### User Information:
1. **Your name**: Enter your full name
2. **Computer name**: Auto-filled (can be changed)
3. **Username**: Choose a username (lowercase, no spaces)
4. **Password**: Create a strong password
5. **Confirm password**: Re-enter password
6. Choose login option:
   - **Log in automatically** (convenient for VMs)
   - **Require password to log in** (more secure)
7. Click **"Continue"**

#### Installation Progress:
1. Ubuntu will now install (15-30 minutes)
2. You'll see a slideshow explaining Ubuntu features
3. **Don't close the VM or power off during installation**

#### Installation Complete:
1. Click **"Restart Now"**
2. Press `Enter` when prompted to remove installation medium
3. VM will restart into your new Ubuntu system

---

## Post-Installation Setup

### Step 1: First Boot
1. **Login screen**: Enter your password
2. **Welcome screen**: 
   - Skip or go through the setup wizard
   - Choose whether to send system data
   - Connect online accounts (optional)

### Step 2: Update System
```bash
# Open Terminal (Ctrl+Alt+T)
sudo apt update
sudo apt upgrade -y
```

### Step 3: Install Essential Software
```bash
# Development tools
sudo apt install -y curl wget git vim nano build-essential

# Media codecs
sudo apt install -y ubuntu-restricted-extras

# Useful utilities
sudo apt install -y htop tree neofetch
```

---

## VirtualBox Guest Additions

Guest Additions improve VM performance and enable features like:
- Better screen resolution
- Seamless mouse integration
- Shared folders
- Clipboard sharing
- Drag and drop files

### Installation Method 1: Using VirtualBox Menu

1. **Start your Ubuntu VM**
2. **Log in** to Ubuntu
3. In VirtualBox menu: **Devices** → **Insert Guest Additions CD image**
4. Ubuntu will prompt to run the software
5. Click **"Run"** and enter your password
6. Wait for installation to complete
7. **Restart** the VM

### Installation Method 2: Terminal Method

```bash
# Update system first
sudo apt update

# Install prerequisites
sudo apt install -y build-essential dkms linux-headers-generic

# Mount the Guest Additions CD (if not auto-mounted)
sudo mkdir -p /mnt/cdrom
sudo mount /dev/cdrom /mnt/cdrom

# Run the installation
cd /mnt/cdrom
sudo ./VBoxLinuxAdditions.run

# Reboot system
sudo reboot
```

### Verify Installation
```bash
# Check if Guest Additions are loaded
lsmod | grep vbox
```

---

## Troubleshooting

### Common Issues and Solutions

#### 1. VM Won't Start - "VT-x is disabled"
**Solution:**
1. **Restart computer**
2. **Enter BIOS/UEFI** (usually F2, F12, or Delete during boot)
3. **Find Virtualization settings** (Intel VT-x or AMD-V)
4. **Enable** the setting
5. **Save and exit** BIOS

#### 2. VM is Very Slow
**Solutions:**
- Increase RAM allocation (Settings → System → Motherboard)
- Enable 3D acceleration (Settings → Display)
- Increase video memory to 128MB
- Install Guest Additions
- Close unnecessary host applications

#### 3. Screen Resolution Issues
**Solutions:**
1. Install Guest Additions
2. In Ubuntu: Settings → Displays → Choose resolution
3. VirtualBox menu: View → Auto-resize Guest Display

#### 4. No Internet in VM
**Solutions:**
1. VM Settings → Network → Adapter 1
2. Ensure "Enable Network Adapter" is checked
3. Attached to: NAT (default) or Bridged Adapter
4. Advanced → Cable Connected: checked

#### 5. Shared Folders Not Working
**Setup Shared Folders:**
1. VM Settings → Shared Folders
2. Add folder: Machine Folders → Add (+)
3. Folder Path: Choose host folder
4. Folder Name: Give it a name
5. ✅ Auto-mount, ✅ Make Permanent
6. In Ubuntu:
```bash
# Add user to vboxsf group
sudo usermod -aG vboxsf $USER
# Logout and login again
```

#### 6. Audio Not Working
**Solution:**
1. VM Settings → Audio
2. Enable Audio: ✅
3. Host Audio Driver: Choose appropriate (PulseAudio for Linux)
4. Audio Controller: Intel HD Audio

---

## Best Practices

### Performance Optimization

#### Host System:
- **Close unnecessary applications** before running VMs
- **Disable host antivirus real-time scanning** for VM files
- **Use SSD storage** for better performance
- **Keep host system updated**

#### VM Settings:
- **Don't over-allocate resources** (stay in green zones)
- **Enable hardware acceleration** when available
- **Use paravirtualization interface**: KVM for Linux guests
- **Adjust video memory** based on usage (128MB for desktop)

### Security Best Practices

#### VM Isolation:
- **Use snapshots** before major changes
- **Regular backups** of important VMs
- **Network isolation** for testing potentially harmful software
- **Keep VMs updated** with security patches

#### Snapshots:
```
Right-click VM → Snapshots → Take Snapshot
```
- Create snapshots before:
  - Installing new software
  - System updates
  - Configuration changes
  - Testing potentially harmful code

### Resource Management

#### Storage:
- **Use dynamic allocation** for disk space
- **Regular cleanup** of unnecessary files
- **Compress VDI files** when VM is powered off:
```bash
# From host command line
VBoxManage modifymedium disk "path/to/vm.vdi" --compact
```

#### Memory:
- **Monitor host RAM usage** while VM is running
- **Don't run multiple heavy VMs** simultaneously
- **Consider VM priorities** if running multiple VMs

### Backup Strategy

#### Export VMs:
1. **File** → **Export Appliance**
2. Select VMs to export
3. Choose export format (OVF recommended)
4. Specify export location

#### Clone VMs:
1. **Right-click VM** → **Clone**
2. **Full clone**: Independent copy
3. **Linked clone**: Shares disk with original (faster, less space)

---

## Quick Reference Commands

### VirtualBox CLI Commands (VBoxManage)
```bash
# List all VMs
VBoxManage list vms

# Start VM headless
VBoxManage startvm "VM-Name" --type headless

# Power off VM
VBoxManage controlvm "VM-Name" poweroff

# Create snapshot
VBoxManage snapshot "VM-Name" take "snapshot-name"

# Restore snapshot
VBoxManage snapshot "VM-Name" restore "snapshot-name"
```

### Ubuntu Essential Commands
```bash
# System information
neofetch
lsb_release -a

# Update system
sudo apt update && sudo apt upgrade

# Install software
sudo apt install package-name

# Check disk usage
df -h

# Check memory usage
free -h

# Process monitoring
htop

# Network information
ip addr show
```

---

## Conclusion

You now have a fully functional Ubuntu virtual machine running on VirtualBox! This setup provides:

- **Safe testing environment** for learning Linux
- **Isolated system** for development and experimentation
- **Snapshot capability** for easy recovery
- **Cross-platform compatibility** for different host operating systems

### Next Steps:
1. **Explore Ubuntu desktop** and get familiar with the interface
2. **Practice basic Linux commands** in the terminal
3. **Create snapshots** before making major changes
4. **Install development tools** based on your learning path
5. **Set up shared folders** for easy file transfer

### Additional Learning Resources:
- Ubuntu Documentation: [https://help.ubuntu.com/](https://help.ubuntu.com/)
- VirtualBox Manual: [https://www.virtualbox.org/manual/](https://www.virtualbox.org/manual/)
- Linux Journey: [https://linuxjourney.com/](https://linuxjourney.com/)

**Happy learning and welcome to the world of Linux!** 🐧