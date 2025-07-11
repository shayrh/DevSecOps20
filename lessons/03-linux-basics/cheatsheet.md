# DevOps Quick Reference Cheatsheet

## Number Systems
```bash
# Binary (Base 2): 0, 1
13 decimal = 1101 binary
1101 binary = 13 decimal

# Hexadecimal (Base 16): 0-9, A-F
255 decimal = FF hex
FF hex = 255 decimal
```

## User Management
```bash
# Create/Delete Users
sudo useradd -m username          # Create with home dir
sudo userdel -r username          # Delete with home dir
sudo passwd username              # Set password

# Modify Users
sudo usermod -a -G group user     # Add to group
sudo usermod -L username          # Lock account
sudo usermod -U username          # Unlock account

# Information
whoami                            # Current user
id                               # User/group IDs
groups username                   # User's groups
cat /etc/passwd                   # All users
```

## Group Management
```bash
# Create/Delete Groups
sudo groupadd groupname           # Create group
sudo groupdel groupname           # Delete group

# Modify Groups
sudo gpasswd -a user group        # Add user to group
sudo gpasswd -d user group        # Remove user from group
cat /etc/group                    # All groups
```

## File Permissions
```bash
# Permission Structure: drwxrwxrwx
# d = directory, - = file, l = link
# rwx = read(4) write(2) execute(1)

# Common Permissions
755 = rwxr-xr-x    # Executable files
644 = rw-r--r--    # Regular files
600 = rw-------    # Private files
777 = rwxrwxrwx    # Full access (avoid!)

# chmod Commands
chmod 755 file              # Numeric
chmod u+x file              # Add execute for user
chmod g-w file              # Remove write for group
chmod o=r file              # Set other to read-only
chmod -R 755 directory/     # Recursive

# chown Commands
sudo chown user file              # Change owner
sudo chown user:group file        # Change owner:group
sudo chown -R user:group dir/     # Recursive
```

## Sudo & System Files
```bash
# Sudo
sudo command                # Run as root
sudo -u user command        # Run as specific user
sudo -l                     # List permissions
sudo visudo                 # Edit sudoers file

# Add user to sudo group
sudo usermod -a -G sudo username

# /etc/passwd format:
# username:x:UID:GID:comment:home:shell
```

## I/O Redirection
```bash
# Standard Streams
# 0 = stdin, 1 = stdout, 2 = stderr

# Redirection
command > file              # Stdout to file
command 2> file             # Stderr to file
command &> file             # Both to file
command >> file             # Append to file
command < file              # Input from file

# Piping
command1 | command2         # Pipe output
command | tee file          # Copy to file and stdout
command | tee -a file       # Append to file and stdout
```

## Text Processing
```bash
# cut - Extract columns
cut -c 1-5 file             # Characters 1-5
cut -d':' -f1 file          # Field 1 (delimiter :)
cut -d',' -f1,3 file        # Fields 1 and 3

# wc - Count lines/words/chars
wc file                     # Lines, words, chars
wc -l file                  # Lines only
wc -w file                  # Words only
wc -c file                  # Characters only

# grep - Search text
grep "pattern" file         # Basic search
grep -i "pattern" file      # Case insensitive
grep -n "pattern" file      # Show line numbers
grep -r "pattern" dir/      # Recursive search

# sort & uniq
sort file                   # Sort lines
sort -n file                # Numeric sort
sort -r file                # Reverse sort
uniq file                   # Remove duplicates
uniq -c file                # Count occurrences
```

## Quick Examples
```bash
# Count users in system
cut -d':' -f1 /etc/passwd | wc -l

# Find most used commands
history | cut -d' ' -f4 | sort | uniq -c | sort -nr | head -10

# Create user with home and set password
sudo useradd -m newuser && sudo passwd newuser

# Set file permissions for web content
chmod 644 *.html && chmod 755 *.sh

# Search and count errors in log
grep "ERROR" /var/log/syslog | wc -l

# Display file permissions
ls -la | cut -d' ' -f1

# Backup command output
ps aux | tee process_backup.txt | grep python
```

## Permission Quick Reference
| Octal | Binary | Symbolic | Description |
|-------|--------|----------|-------------|
| 0     | 000    | ---      | No permissions |
| 1     | 001    | --x      | Execute only |
| 2     | 010    | -w-      | Write only |
| 3     | 011    | -wx      | Write + Execute |
| 4     | 100    | r--      | Read only |
| 5     | 101    | r-x      | Read + Execute |
| 6     | 110    | rw-      | Read + Write |
| 7     | 111    | rwx      | Full permissions |

## Special Characters
```bash
|   # Pipe
>   # Redirect output
>>  # Append output
<   # Input redirect
&   # Background process
*   # Wildcard (any characters)
?   # Wildcard (single character)
~   # Home directory
.   # Current directory
..  # Parent directory
```