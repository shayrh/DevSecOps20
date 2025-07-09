# Linux Basics - Comprehensive Guide

## Table of Contents
1. [Virtual Machines](#virtual-machines)
2. [Shell and Bash](#shell-and-bash)
3. [The Terminal and Command Prompt](#the-terminal-and-command-prompt)
4. [User Privileges: $ vs #](#user-privileges--vs-)
5. [Package Management with APT](#package-management-with-apt)
6. [Navigation Commands](#navigation-commands)
7. [File Operations](#file-operations)
8. [Process Management](#process-management)
9. [Input/Output Redirection](#inputoutput-redirection)
10. [Exit Codes](#exit-codes)
11. [Environment Variables and PATH](#environment-variables-and-path)
12. [How the Terminal Works](#how-the-terminal-works)
13. [Linux File System Structure](#linux-file-system-structure)
14. [Additional Essential Concepts](#additional-essential-concepts)

---

## Virtual Machines

### What is a Virtual Machine?
A virtual machine (VM) is a software-based computer that runs inside your physical computer. It creates a complete, isolated operating system environment that shares the hardware resources of the host machine.

### Key Concepts:
- **Host OS**: The operating system running on your physical machine
- **Guest OS**: The operating system running inside the VM (in our case, Linux)
- **Hypervisor**: Software that manages VMs (VMware, VirtualBox, etc.)
- **Virtualization**: The technology that allows multiple OS instances to run on one machine

### Benefits:
- Safe testing environment
- Isolation from host system
- Easy snapshots and backups
- Multiple OS environments on one machine
- Consistent development environments across teams

### Common VM Software:
- **VirtualBox** (free, cross-platform)
- **VMware Workstation/Fusion** (paid, feature-rich)
- **Hyper-V** (Windows built-in)
- **QEMU/KVM** (Linux native)

---

## Shell and Bash

### What is a Shell?
A shell is a command-line interface that interprets and executes commands. It acts as an intermediary between you and the operating system kernel.

### Bash (Bourne Again Shell)
Bash is the most common shell in Linux distributions. It's an enhanced version of the original Bourne shell (sh).

### Key Features:
- **Command history**: Use arrow keys to navigate previous commands
- **Tab completion**: Press Tab to auto-complete commands and filenames
- **Command substitution**: Use `$(command)` or backticks
- **Variables**: Store and use values
- **Scripts**: Write executable files with multiple commands

### Other Common Shells:
- **sh** (Bourne Shell) - Original shell
- **zsh** (Z Shell) - Feature-rich, popular alternative
- **fish** (Friendly Interactive Shell) - User-friendly
- **dash** (Debian Almquist Shell) - Lightweight

### Check Your Current Shell:
```bash
echo $SHELL
```

---

## The Terminal and Command Prompt

### Understanding the Prompt
The terminal prompt provides important information about your current session:

```bash
user@machine:~$
```

**Breaking it down:**
- `user` - Your username
- `@` - Separator
- `machine` - Hostname/computer name
- `:` - Separator
- `~` - Current directory (~ represents home directory)
- `$` - Indicates regular user (vs # for root)

### Prompt Examples:
```bash
john@ubuntu:~$ 
john@ubuntu:/home/john/documents$ 
john@ubuntu:/etc$ 
```

### Customizing Your Prompt:
The prompt is controlled by the `PS1` environment variable:
```bash
echo $PS1
export PS1="\u@\h:\w\$ "
```

---

## User Privileges: $ vs #

### The Dollar Sign ($)
- Indicates you're logged in as a **regular user**
- Limited permissions
- Cannot modify system files
- Safe for everyday tasks

### The Hash/Pound Sign (#)
- Indicates you're logged in as **root** (superuser)
- Full system access
- Can modify any file
- **Dangerous** - use carefully!

### Switching Between Users:
```bash
# Switch to root (if allowed)
sudo su -

# Switch to another user
su - username

# Run single command as root
sudo command

# Return to regular user
exit
```

### Best Practices:
- **Never** work as root for daily tasks
- Use `sudo` for administrative commands
- Always double-check commands when you see `#`

---

## Package Management with APT

### What is APT?
APT (Advanced Package Tool) is Debian/Ubuntu's package management system. It handles software installation, updates, and removal.

### Common APT Commands:

#### Update Package Lists:
```bash
sudo apt update
```

#### Upgrade Installed Packages:
```bash
sudo apt upgrade
sudo apt full-upgrade  # More comprehensive
```

#### Install Software:
```bash
sudo apt install package_name
sudo apt install vim git curl
```

#### Remove Software:
```bash
sudo apt remove package_name
sudo apt purge package_name    # Removes config files too
```

#### Search for Packages:
```bash
apt search keyword
apt list --installed
```

#### Get Package Information:
```bash
apt show package_name
```

#### Clean Package Cache:
```bash
sudo apt autoremove  # Remove unused dependencies
sudo apt autoclean   # Clean package cache
```

### Package Sources:
- Configuration in `/etc/apt/sources.list`
- Additional sources in `/etc/apt/sources.list.d/`

---

## Navigation Commands

### pwd - Print Working Directory
Shows your current location in the file system:
```bash
pwd
# Output: /home/username/documents
```

### ls - List Directory Contents
Basic listing:
```bash
ls                    # Basic listing
ls -l                 # Long format (detailed)
ls -a                 # Show hidden files
ls -h                 # Human-readable sizes
ls -lah               # Combination of all above
ll                    # Alias for ls -l (on many systems)
```

### Understanding ls -lah Output:
```bash
drwxr-xr-x  2 user user 4.0K Jan 15 10:30 documents
-rw-r--r--  1 user user  1.2K Jan 15 09:45 file.txt
```

**Breaking it down:**
- `d` = directory, `-` = file
- `rwxr-xr-x` = permissions (owner, group, others)
- `2` = number of links
- `user user` = owner and group
- `4.0K` = size
- `Jan 15 10:30` = last modified date/time
- `documents` = name

### cd - Change Directory
```bash
cd /path/to/directory    # Absolute path
cd documents            # Relative path
cd ..                   # Go up one directory
cd ../..                # Go up two directories
cd ~                    # Go to home directory
cd -                    # Go to previous directory
cd /                    # Go to root directory
```

### mkdir - Create Directories
```bash
mkdir directory_name
mkdir -p path/to/new/directory  # Create parent directories
mkdir dir1 dir2 dir3            # Create multiple directories
```

---

## File Operations

### cp - Copy Files and Directories
```bash
cp source destination
cp file.txt backup.txt
cp -r directory/ backup_directory/  # Recursive for directories
cp -i file.txt dest.txt             # Interactive (prompt before overwrite)
cp -u source dest                   # Update (copy only if newer)
```

### mv - Move/Rename Files and Directories
```bash
mv old_name new_name              # Rename
mv file.txt /path/to/destination/ # Move
mv *.txt documents/               # Move multiple files
```

### rm - Remove Files and Directories
```bash
rm file.txt                       # Remove file
rm -r directory/                  # Remove directory recursively
rm -i file.txt                    # Interactive removal
rm -f file.txt                    # Force removal
rm -rf directory/                 # Force recursive removal (DANGEROUS!)
```

### **Warning**: `rm -rf` is irreversible! Always double-check before using.

### Additional File Operations:
```bash
touch filename.txt                # Create empty file or update timestamp
file filename.txt                 # Determine file type
stat filename.txt                 # Detailed file information
```

---

## Process Management

### ps - Process Status
```bash
ps                      # Show processes for current user
ps aux                  # Show all processes (detailed)
ps -ef                  # Show all processes (different format)
ps -u username          # Show processes for specific user
```

### Understanding ps aux Output:
```bash
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.1  225484  9876 ?        Ss   09:30   0:01 /sbin/init
```

### Other Process Commands:
```bash
top                     # Real-time process viewer
htop                    # Enhanced top (if installed)
jobs                    # Show active jobs
kill PID                # Terminate process by PID
killall process_name    # Kill all processes with name
nohup command &         # Run command immune to hangups
```

### Process States:
- **Running**: Currently executing
- **Sleeping**: Waiting for resource
- **Stopped**: Suspended
- **Zombie**: Finished but not cleaned up

---

## Input/Output Redirection

### Standard Streams
Every process has three standard streams:
- **stdin (0)**: Standard input
- **stdout (1)**: Standard output  
- **stderr (2)**: Standard error

### Output Redirection
```bash
# Redirect stdout to file (overwrite)
echo "Hello World" > output.txt
date > timestamp.txt

# Redirect stdout to file (append)
echo "New line" >> output.txt
date >> timestamp.txt

# Redirect stderr to file
command_that_fails 2> error.txt

# Redirect stdout and stderr to different files
command 1> output.txt 2> error.txt

# Redirect both stdout and stderr to same file
command > output.txt 2>&1
command &> output.txt    # Shorthand
```

### Input Redirection
```bash
# Read from file instead of keyboard
command < input.txt

# Here document (multi-line input)
command << EOF
Line 1
Line 2
EOF
```

### Practical Examples:
```bash
# Save directory listing to file
ls -la > directory_listing.txt

# Append system info to log
uname -a >> system_info.log

# Save only errors from a command
make 2> build_errors.log

# Discard output (send to /dev/null)
command > /dev/null 2>&1
```

---

## Exit Codes

### What are Exit Codes?
Exit codes (return codes) indicate whether a command succeeded or failed:
- **0**: Success
- **1-255**: Various error conditions

### Checking Exit Codes:
```bash
# Run a command
ls /existing/directory

# Check the exit code
echo $?
# Output: 0 (success)

# Try with non-existent directory
ls /nonexistent/directory

# Check the exit code
echo $?
# Output: 2 (error)
```

### Common Exit Codes:
- **0**: Success
- **1**: General error
- **2**: Misuse of shell command
- **126**: Command not executable
- **127**: Command not found
- **128**: Invalid argument to exit
- **130**: Script terminated by Ctrl+C

### Using Exit Codes in Scripts:
```bash
#!/bin/bash
if command; then
    echo "Command succeeded"
else
    echo "Command failed with exit code $?"
fi
```

---

## Environment Variables and PATH

### What are Environment Variables?
Environment variables are dynamic values that affect running processes and programs.

### Common Environment Variables:
```bash
echo $HOME        # Home directory
echo $USER        # Current username
echo $SHELL       # Current shell
echo $PWD         # Current directory
echo $OLDPWD      # Previous directory
echo $PATH        # Command search path
```

### The PATH Variable
PATH tells the shell where to look for executable commands:

```bash
echo $PATH
# Output: /usr/local/bin:/usr/bin:/bin:/usr/games
```

### How Command Execution Works:
1. Shell checks if command is built-in
2. Shell checks if command has absolute path
3. Shell searches directories in PATH (left to right)
4. If found, executes; if not, shows "command not found"

### Modifying PATH:
```bash
# Add directory to PATH (temporary)
export PATH=$PATH:/new/directory

# Add to beginning of PATH (higher priority)
export PATH=/new/directory:$PATH

# Make permanent (add to ~/.bashrc)
echo 'export PATH=$PATH:/new/directory' >> ~/.bashrc
```

### Other Useful Commands:
```bash
which command_name    # Show full path of command
type command_name     # Show command type (alias, function, etc.)
env                   # Show all environment variables
set                   # Show all variables (including local)
```

---

## How the Terminal Works

### The Process Flow:
1. **Terminal Emulator**: Provides the graphical interface
2. **Shell**: Interprets and executes commands
3. **Kernel**: Manages system resources and hardware
4. **Programs**: Execute and return results

### Terminal vs Console vs Shell:
- **Terminal**: The interface (physical or emulated)
- **Console**: System's text input/output environment
- **Shell**: Command interpreter program

### Terminal Emulators:
- **GNOME Terminal** (Ubuntu default)
- **Konsole** (KDE)
- **xterm** (X Window System)
- **Terminator** (Advanced features)

### Key Concepts:
- **TTY**: Teletypewriter (terminal device)
- **PTY**: Pseudo-terminal (software emulation)
- **Session**: Group of related processes
- **Job Control**: Managing foreground/background processes

### Terminal Shortcuts:
```bash
Ctrl+C    # Interrupt current command
Ctrl+D    # End of file (logout)
Ctrl+Z    # Suspend current job
Ctrl+L    # Clear screen
Ctrl+A    # Move to beginning of line
Ctrl+E    # Move to end of line
Ctrl+R    # Reverse search history
```

---

## Linux File System Structure

### Hierarchical Structure
Linux uses a tree-like directory structure starting from root (`/`):

```
/
├── bin/          # Essential user binaries
├── boot/         # Boot loader files
├── dev/          # Device files
├── etc/          # System configuration files
├── home/         # User home directories
├── lib/          # Essential shared libraries
├── media/        # Removable media mount points
├── mnt/          # Temporary mount points
├── opt/          # Optional software packages
├── proc/         # Process information (virtual)
├── root/         # Root user's home directory
├── run/          # Runtime data
├── sbin/         # System binaries
├── srv/          # Service data
├── sys/          # System information (virtual)
├── tmp/          # Temporary files
├── usr/          # User programs and data
└── var/          # Variable data (logs, etc.)
```

### Key Directory Explanations:

#### `/bin` - Essential Binaries
Contains essential command-line programs needed for basic system operation:
```bash
ls /bin
# Contains: ls, cp, mv, rm, bash, etc.
```

#### `/etc` - Configuration Files
System-wide configuration files:
```bash
/etc/passwd       # User account information
/etc/fstab        # File system mount information
/etc/hosts        # Host name resolution
/etc/ssh/         # SSH configuration
```

#### `/home` - User Directories
Each user has a subdirectory here:
```bash
/home/john/       # John's home directory
/home/mary/       # Mary's home directory
```

#### `/usr` - User Programs
Secondary hierarchy for user programs:
```bash
/usr/bin/         # Non-essential user binaries
/usr/lib/         # Libraries for /usr/bin
/usr/local/       # Locally installed software
/usr/share/       # Shared data (documentation, etc.)
```

#### `/var` - Variable Data
Files that change during normal operation:
```bash
/var/log/         # Log files
/var/tmp/         # Temporary files (preserved between reboots)
/var/mail/        # Mail files
/var/www/         # Web server files
```

### File System Types:
- **ext4**: Default Linux file system
- **xfs**: High-performance file system
- **btrfs**: Copy-on-write file system
- **ntfs**: Windows file system (readable)
- **fat32**: Cross-platform compatibility

### File Permissions:
```bash
drwxr-xr-x
```
- **d**: Directory (- for file)
- **rwx**: Owner permissions (read, write, execute)
- **r-x**: Group permissions
- **r-x**: Others permissions

### Permission Numbers:
- **r** = 4, **w** = 2, **x** = 1
- **755** = rwxr-xr-x (owner full, group/others read+execute)
- **644** = rw-r--r-- (owner read/write, group/others read)

---

## Additional Essential Concepts

### File Permissions and Ownership

#### Viewing Permissions:
```bash
ls -l filename
stat filename
```

#### Changing Permissions:
```bash
chmod 755 filename              # Numeric method
chmod u+x filename              # Symbolic method (user execute)
chmod g-w filename              # Remove group write
chmod o=r filename              # Set others to read only
```

#### Changing Ownership:
```bash
sudo chown user:group filename
sudo chown user filename        # Change owner only
sudo chgrp group filename       # Change group only
```

### Text Processing Commands

#### cat - Display File Contents:
```bash
cat filename.txt
cat file1.txt file2.txt         # Concatenate files
cat > newfile.txt               # Create file with input
```

#### less/more - View Files Page by Page:
```bash
less filename.txt               # Better than more
more filename.txt               # Basic pager
```

#### head/tail - View Beginning/End of Files:
```bash
head -n 10 filename.txt         # First 10 lines
tail -n 10 filename.txt         # Last 10 lines
tail -f logfile.txt             # Follow file changes
```

#### grep - Search Text:
```bash
grep "pattern" filename.txt
grep -r "pattern" directory/    # Recursive search
grep -i "pattern" filename.txt  # Case insensitive
grep -n "pattern" filename.txt  # Show line numbers
```

### Archives and Compression

#### tar - Archive Files:
```bash
tar -czf archive.tar.gz files/  # Create compressed archive
tar -xzf archive.tar.gz         # Extract compressed archive
tar -tzf archive.tar.gz         # List contents
```

#### zip/unzip:
```bash
zip archive.zip files/
unzip archive.zip
```

### Network Commands

#### ping - Test Network Connectivity:
```bash
ping google.com
ping -c 4 google.com            # Send 4 packets
```

#### wget/curl - Download Files:
```bash
wget https://example.com/file.txt
curl -O https://example.com/file.txt
```

### System Information

#### System Info Commands:
```bash
uname -a                        # System information
whoami                          # Current user
id                              # User and group IDs
date                            # Current date and time
uptime                          # System uptime
df -h                           # Disk space usage
du -sh directory/               # Directory size
free -h                         # Memory usage
lscpu                           # CPU information
```

### Keyboard Shortcuts and Tips

#### Essential Shortcuts:
```bash
Tab                             # Auto-complete
Ctrl+C                          # Cancel current command
Ctrl+D                          # Exit/logout
Ctrl+L                          # Clear screen
Ctrl+A                          # Move to start of line
Ctrl+E                          # Move to end of line
Ctrl+U                          # Delete line before cursor
Ctrl+K                          # Delete line after cursor
Ctrl+R                          # Search command history
!!                              # Repeat last command
!n                              # Run command number n from history
```

#### Command History:
```bash
history                         # Show command history
history | grep "pattern"        # Search history
```



### Best Practices

1. **Always use Tab completion** to avoid typos
2. **Use `ls -la` frequently** to understand your environment
3. **Check `pwd` regularly** to know your location
4. **Use `--help` or `man command`** to learn about commands
5. **Practice with non-critical files** first
6. **Keep backups** of important files
7. **Use `sudo` carefully** and only when necessary
8. **Read error messages** - they often contain helpful information

---

## Summary

This guide covers the fundamental concepts of Linux that every user should understand:

- **Virtual Machines** provide safe learning environments
- **Bash** is your command interpreter and scripting language
- **Terminal prompts** give you important context information
- **User privileges** (`$` vs `#`) determine what you can do
- **APT** manages software packages efficiently
- **Navigation and file operations** are essential daily tasks
- **Process management** helps you control running programs
- **I/O redirection** allows flexible command chaining
- **Exit codes** indicate command success or failure
- **PATH** determines where the shell finds commands
- **File system structure** provides organization and hierarchy

Practice these concepts regularly, and you'll become proficient in Linux administration and daily usage. Remember that the `man` command (manual pages) is your best friend for learning more about any command:

```bash
man ls
man grep
man bash
```

Happy learning!