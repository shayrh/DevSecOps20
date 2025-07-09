# Linux Basic Commands Cheatsheet

## Navigation Commands

### `pwd` - Print Working Directory
**What it does**: Shows your current location in the file system

```bash
pwd
```

**Example Output**: `/home/username/documents`

---

### `ls` - List Directory Contents
**What it does**: Lists files and directories in the current or specified directory

```bash
ls [options] [directory]
```

**Common Flags**:
- `-l` - Long format (detailed listing)
- `-a` - Show all files (including hidden files starting with .)
- `-h` - Human-readable file sizes (use with -l)
- `-r` - Reverse order
- `-t` - Sort by modification time
- `-S` - Sort by file size
- `-R` - Recursive listing

**Most Used Combinations**:
```bash
ls                    # Basic listing
ls -l                 # Long format
ls -la                # Long format with hidden files
ls -lah               # Long format, hidden files, human-readable sizes
ls -ltr               # Long format, sorted by time (newest last)
```

**Alias**: `ll` (usually equals `ls -l`)

---

### `cd` - Change Directory
**What it does**: Changes your current working directory

```bash
cd [directory]
```

**Common Usage**:
```bash
cd /path/to/directory    # Go to absolute path
cd documents            # Go to relative path
cd ..                   # Go up one directory
cd ../..                # Go up two directories
cd ~                    # Go to home directory
cd -                    # Go to previous directory
cd /                    # Go to root directory
cd                      # Go to home directory (same as cd ~)
```

---

## File and Directory Operations

### `mkdir` - Make Directory
**What it does**: Creates new directories

```bash
mkdir [options] directory_name
```

**Common Flags**:
- `-p` - Create parent directories as needed
- `-m` - Set file permissions
- `-v` - Verbose output

**Examples**:
```bash
mkdir newdir                    # Create single directory
mkdir dir1 dir2 dir3           # Create multiple directories
mkdir -p path/to/new/directory # Create nested directories
mkdir -v testdir               # Create with verbose output
```

---

### `cp` - Copy Files and Directories
**What it does**: Copies files or directories to another location

```bash
cp [options] source destination
```

**Common Flags**:
- `-r` or `-R` - Recursive (for directories)
- `-i` - Interactive (prompt before overwrite)
- `-u` - Update (copy only if newer)
- `-v` - Verbose output
- `-p` - Preserve file attributes
- `-a` - Archive mode (preserve everything)

**Examples**:
```bash
cp file.txt backup.txt              # Copy file
cp -r directory/ backup_directory/  # Copy directory
cp -i file.txt dest.txt             # Interactive copy
cp -u source.txt dest.txt           # Update only if newer
cp *.txt backup/                    # Copy all .txt files
```

---

### `mv` - Move/Rename Files and Directories
**What it does**: Moves files/directories to new location or renames them

```bash
mv [options] source destination
```

**Common Flags**:
- `-i` - Interactive (prompt before overwrite)
- `-u` - Update (move only if newer)
- `-v` - Verbose output
- `-n` - No overwrite

**Examples**:
```bash
mv oldname.txt newname.txt          # Rename file
mv file.txt /path/to/destination/   # Move file
mv directory/ /new/location/        # Move directory
mv -i file.txt dest.txt             # Interactive move
mv *.txt documents/                 # Move all .txt files
```

---

### `rm` - Remove Files and Directories
**What it does**: Deletes files and directories

```bash
rm [options] file_or_directory
```

**Common Flags**:
- `-r` or `-R` - Recursive (for directories)
- `-f` - Force (no prompts)
- `-i` - Interactive (prompt for each file)
- `-v` - Verbose output

**Examples**:
```bash
rm file.txt                    # Remove file
rm -r directory/               # Remove directory recursively
rm -i file.txt                 # Interactive removal
rm -f file.txt                 # Force removal
rm -rf directory/              # Force recursive removal (DANGEROUS!)
rm *.tmp                       # Remove all .tmp files
```

⚠️ **Warning**: `rm -rf` is irreversible! Always double-check before using.

---

## Process Management

### `ps` - Process Status
**What it does**: Shows information about running processes

```bash
ps [options]
```

**Common Flags**:
- `aux` - Show all processes for all users
- `-ef` - Show all processes in full format
- `-u username` - Show processes for specific user
- `-f` - Full format listing
- `-x` - Show processes not attached to terminal

**Examples**:
```bash
ps                      # Show processes for current user
ps aux                  # Show all processes (most common)
ps -ef                  # Show all processes (alternative format)
ps -u john              # Show processes for user 'john'
ps aux | grep firefox   # Find Firefox processes
```

**Understanding ps aux output**:
```
USER  PID %CPU %MEM    VSZ   RSS TTY   STAT START   TIME COMMAND
john  1234  0.5  2.1  12345  8765 pts/0  S+   10:30   0:05 firefox
```

---

## Package Management (APT)

### `apt` - Advanced Package Tool
**What it does**: Manages software packages (install, remove, update)

```bash
sudo apt [command] [options] [package_name]
```

**Common Commands**:
```bash
sudo apt update                    # Update package lists
sudo apt upgrade                   # Upgrade installed packages
sudo apt install package_name     # Install package
sudo apt remove package_name      # Remove package
sudo apt purge package_name       # Remove package and config files
sudo apt autoremove               # Remove unused dependencies
sudo apt autoclean                # Clean package cache
```

**Search and Information**:
```bash
apt search keyword                 # Search for packages
apt show package_name             # Show package information
apt list --installed              # List installed packages
apt list --upgradable             # List upgradable packages
```

---

## Input/Output Redirection

### Output Redirection
**What it does**: Redirects command output to files or other destinations

```bash
command > file.txt         # Redirect stdout to file (overwrite)
command >> file.txt        # Redirect stdout to file (append)
command 2> error.txt       # Redirect stderr to file
command 2>> error.txt      # Redirect stderr to file (append)
command > output.txt 2>&1  # Redirect both stdout and stderr to file
command &> output.txt      # Redirect both stdout and stderr (shorthand)
command > /dev/null 2>&1   # Discard all output
```

### Input Redirection
**What it does**: Redirects input from files instead of keyboard

```bash
command < input.txt        # Read input from file
```

**Practical Examples**:
```bash
ls -la > directory_list.txt       # Save directory listing
date >> log.txt                   # Append timestamp to log
echo "Hello" > greeting.txt       # Write text to file
cat nonexistent.txt 2> error.log  # Save error to file
```

---

## System Information Commands

### `date` - Display or Set Date
**What it does**: Shows current date and time

```bash
date [options] [format]
```

**Examples**:
```bash
date                          # Current date and time
date +"%Y-%m-%d"             # Format: 2024-01-15
date +"%H:%M:%S"             # Format: 14:30:25
date >> timestamp.log        # Append timestamp to log
```

---

### `echo` - Display Text
**What it does**: Prints text to stdout

```bash
echo [options] "text"
```

**Common Flags**:
- `-n` - No trailing newline
- `-e` - Enable interpretation of backslash escapes

**Examples**:
```bash
echo "Hello World"              # Print text
echo -n "No newline"            # Print without newline
echo "Text" > file.txt          # Write text to file
echo "More text" >> file.txt    # Append text to file
echo $PATH                      # Print environment variable
```

---

## Environment and Variables

### Environment Variables
**What they do**: Store system and user configuration information

```bash
echo $VARIABLE_NAME           # Display variable value
```

**Common Variables**:
```bash
echo $PATH                    # Command search path
echo $HOME                    # User home directory
echo $USER                    # Current username
echo $SHELL                   # Current shell
echo $PWD                     # Current directory
echo $?                       # Exit code of last command
```

### `export` - Set Environment Variables
**What it does**: Creates or modifies environment variables

```bash
export VARIABLE_NAME=value
```

**Examples**:
```bash
export PATH=$PATH:/new/directory    # Add to PATH
export EDITOR=vim                   # Set default editor
export JAVA_HOME=/usr/lib/jvm/java  # Set Java home
```

---

## Exit Codes

### `$?` - Last Command Exit Code
**What it does**: Shows the exit status of the last executed command

```bash
command
echo $?
```

**Exit Code Meanings**:
- `0` - Success
- `1` - General error
- `2` - Misuse of shell command
- `126` - Command not executable
- `127` - Command not found

**Example**:
```bash
ls /existing/directory
echo $?                    # Output: 0 (success)

ls /nonexistent/directory
echo $?                    # Output: 2 (error)
```

---

## File Viewing and Text Operations

### `cat` - Display File Contents
**What it does**: Displays the contents of files

```bash
cat [options] file
```

**Common Flags**:
- `-n` - Number lines
- `-b` - Number non-blank lines
- `-s` - Squeeze multiple blank lines

**Examples**:
```bash
cat file.txt                  # Display file contents
cat file1.txt file2.txt      # Display multiple files
cat -n file.txt              # Display with line numbers
cat > newfile.txt            # Create file with keyboard input
```

---

### `less` - View File Contents Page by Page
**What it does**: Views file contents with navigation (better than `more`)

```bash
less file.txt
```

**Navigation inside less**:
- `Space` or `f` - Next page
- `b` - Previous page
- `q` - Quit
- `/pattern` - Search forward
- `?pattern` - Search backward
- `G` - Go to end
- `g` - Go to beginning

---

### `head` - Display First Lines
**What it does**: Shows the first lines of a file

```bash
head [options] file
```

**Common Flags**:
- `-n number` - Show specific number of lines
- `-c number` - Show specific number of characters

**Examples**:
```bash
head file.txt               # Show first 10 lines (default)
head -n 5 file.txt         # Show first 5 lines
head -20 file.txt          # Show first 20 lines
```

---

### `tail` - Display Last Lines
**What it does**: Shows the last lines of a file

```bash
tail [options] file
```

**Common Flags**:
- `-n number` - Show specific number of lines
- `-f` - Follow file changes (useful for logs)
- `-c number` - Show specific number of characters

**Examples**:
```bash
tail file.txt               # Show last 10 lines (default)
tail -n 5 file.txt         # Show last 5 lines
tail -f /var/log/syslog    # Follow log file changes
```

---

## Command Help and Documentation

### `man` - Manual Pages
**What it does**: Shows detailed documentation for commands

```bash
man command_name
```

**Examples**:
```bash
man ls                      # Show ls manual
man grep                    # Show grep manual
man man                     # Show man manual
```

### `--help` Flag
**What it does**: Shows quick help for most commands

```bash
command --help
```

**Examples**:
```bash
ls --help                   # Quick help for ls
cp --help                   # Quick help for cp
```

---

## File Permissions

### `chmod` - Change File Permissions
**What it does**: Changes file and directory permissions

```bash
chmod [permissions] file
```

**Numeric Method**:
- `4` = read (r)
- `2` = write (w)  
- `1` = execute (x)

**Examples**:
```bash
chmod 755 file.txt          # rwxr-xr-x
chmod 644 file.txt          # rw-r--r--
chmod +x script.sh          # Add execute permission
chmod -w file.txt           # Remove write permission
```

---

## Quick Reference Summary

### Most Essential Commands:
```bash
pwd                         # Where am I?
ls -la                      # What's here?
cd directory               # Go somewhere
mkdir newdir               # Create directory
cp file backup             # Copy file
mv file newname            # Move/rename
rm file                    # Delete file
ps aux                     # Show processes
echo "text" > file.txt     # Write to file
echo $?                    # Check last command status
```

### Common Patterns:
```bash
ls -la > listing.txt       # Save directory listing
date >> log.txt            # Append timestamp
command 2> error.txt       # Save errors
command > /dev/null 2>&1   # Discard all output
```

### Remember:
- Use `Tab` for auto-completion
- Use `Ctrl+C` to cancel commands
- Use `man command` for detailed help
- Use `command --help` for quick help
- Check `echo $?` for command success/failure
- Always be careful with `rm -rf`!