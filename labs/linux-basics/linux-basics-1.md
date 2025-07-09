# Linux Basics Lab - 20 Practice Questions

## Instructions
- Complete each question in order
- Test your commands before moving to the next question
- Pay attention to the command prompt ($ vs #)
- Check exit codes when requested
---

## Question 1: Basic Navigation and Information
**Task**: Find out where you are in the file system and display your current username.

**Commands to use**: `pwd`, `whoami`

**Expected actions**:
1. Display your current working directory
2. Display your current username
3. Show what shell you're using

**Write your commands here**:
```bash
# Your commands:


```

---

## Question 2: Directory Listing with Details
**Task**: List all files in your current directory including hidden files, with detailed information and human-readable file sizes.

**Expected output**: Long format listing showing permissions, ownership, file sizes, and modification dates

**Write your command here**:
```bash
# Your command:


```

**Follow-up**: What does the first character in the permissions column tell you?

---

## Question 3: Create Directory Structure
**Task**: Create the following directory structure in one command:
```
workspace/
├── projects/
│   ├── web/
│   └── mobile/
└── documents/
```

**Hint**: Use the `-p` flag

**Write your command here**:
```bash
# Your command:


```

**Verification**: Use `ls -R workspace/` to verify the structure was created correctly.

---

## Question 4: File Creation and Copying
**Task**: 
1. Create a file called `readme.txt` with the content "This is my workspace"
2. Copy this file to the `workspace/documents/` directory
3. Rename the copy to `info.txt`

**Write your commands here**:
```bash
# Your commands:




```

---

## Question 5: Package Management
**Task**: 
1. Update your package lists
2. Search for packages related to "text editor"
3. Show information about the `nano` package (don't install it)

**Write your commands here**:
```bash
# Your commands:




```

---

## Question 6: Process Investigation
**Task**: 
1. Show all running processes in detailed format
2. Find all processes running with your username
3. Count how many processes are running on the system

**Hint**: Use `ps aux`, `grep`, and `wc -l`

**Write your commands here**:
```bash
# Your commands:




```

---

## Question 7: Environment Variables
**Task**: 
1. Display your PATH environment variable
2. Display your home directory path using an environment variable
3. Show the exit code of the previous command

**Write your commands here**:
```bash
# Your commands:




```

---

## Question 8: Output Redirection - Basic
**Task**: 
1. Save the current date and time to a file called `timestamp.txt`
2. Append your username to the same file
3. Display the contents of the file

**Write your commands here**:
```bash
# Your commands:




```

---

## Question 9: Error Redirection
**Task**: 
1. Try to list the contents of a directory that doesn't exist (`/nonexistent`)
2. Save only the error message to a file called `errors.log`
3. Verify that nothing was written to standard output

**Write your commands here**:
```bash
# Your commands:




```

---

## Question 10: Combined Redirection
**Task**: 
1. Run the command `ls /home /nonexistent` 
2. Save successful output to `success.txt` and errors to `errors.txt`
3. Show the exit code of this command

**Write your commands here**:
```bash
# Your commands:




```

---

## Question 11: File Operations and Permissions
**Task**: 
1. Create a file called `script.sh` with the content "echo 'Hello World'"
2. Make it executable
3. Check its permissions using `ls -l`
4. Run the script

**Write your commands here**:
```bash
# Your commands:





```

---

## Question 12: Input Redirection
**Task**: 
1. Create a file called `names.txt` with the following content (each name on a new line):
   ```
   Alice
   Bob
   Charlie
   ```
2. Use the `sort` command to sort the names and save the result to `sorted_names.txt`
3. Use input redirection to feed the file to the sort command

**Write your commands here**:
```bash
# Your commands:




```

---

## Question 13: Multiple File Operations
**Task**: 
1. Copy all `.txt` files from your current directory to `workspace/documents/`
2. Move all files starting with `s` from `workspace/documents/` to `workspace/`
3. Remove any empty directories in `workspace/documents/`

**Write your commands here**:
```bash
# Your commands:




```

---

## Question 14: System Information Collection
**Task**: 
1. Create a system report file called `system_info.txt` that contains:
   - Current date and time
   - Your username
   - Current working directory
   - List of files in your home directory
2. Use redirection to build this file (append each piece of information)

**Write your commands here**:
```bash
# Your commands:






```

---

## Question 15: Error Handling and Exit Codes
**Task**: 
1. Run these commands in sequence and record their exit codes:
   - `ls /home`
   - `ls /root` (this should fail for regular users)
   - `date`
   - `nonexistent_command`
2. Create a file called `exit_codes.txt` with the results

**Write your commands and exit codes here**:
```bash
# Commands and their exit codes:





```

---

## Question 16: File Viewing and Text Processing
**Task**: 
1. View the first 5 lines of `/etc/passwd`
2. View the last 3 lines of `/etc/passwd`
3. Count the total number of lines in `/etc/passwd`
4. Save the line count to a file called `user_count.txt`

**Write your commands here**:
```bash
# Your commands:





```

---

## Question 17: Advanced Redirection
**Task**: 
1. Run the command `find /etc -name "*.conf" 2>/dev/null | head -10`
2. Explain what each part of this command does
3. Save the output to `config_files.txt`

**Write your command here**:
```bash
# Your command:


```

**Explanation**:
```
What does each part do?
- find /etc -name "*.conf": 
- 2>/dev/null: 
- | head -10: 
```

---

## Question 18: Working with Logs
**Task**: 
1. Create a log file called `activity.log`
2. Add the following entries (each with a timestamp):
   - "System started"
   - "User logged in"
   - "Task completed"
3. Display the entire log file with line numbers

**Write your commands here**:
```bash
# Your commands:





```

---

## Question 19: Directory Navigation and Cleanup
**Task**: 
1. Navigate to the deepest directory you created earlier (`workspace/projects/web/`)
2. Create a file called `index.html` there
3. Go back to your home directory using the shortest command
4. Remove the entire `workspace` directory and all its contents
5. Verify it's been deleted

**Write your commands here**:
```bash
# Your commands:






```

---

## Question 20: Comprehensive Challenge
**Task**: Create a script that demonstrates your understanding of all concepts:

1. Create a directory called `lab_final`
2. Inside it, create a file called `system_report.sh` with the following functionality:
   - Display current date and time
   - Display current user and working directory
   - List all files in the current directory
   - Show the PATH variable
   - Display disk usage of the current directory
3. Make the script executable
4. Run the script and save its output to `final_report.txt`
5. Save any errors to `final_errors.txt`
6. Display the exit code

**Write your commands here**:
```bash
# Your commands:








```

