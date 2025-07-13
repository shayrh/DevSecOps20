# Lab 2

# 1: Number Systems

### Tasks:

1. Convert the decimal number `13` to binary.
2. Convert the decimal number `255` to hexadecimal.
3. Convert the binary number `1101` to decimal.
4. Convert the hexadecimal number `FF` to decimal.
5. Write a script that takes a decimal number as input and prints its binary and hexadecimal equivalents.
1.13:2 = 6 reminder 1, 6:2=3 reminder 0, 3:2=1 reminder 1,
2.255:16=15 reminder 
---

## 2: Users and Groups in Ubuntu

### Tasks:

1. Create a new user named `alice`.
2. Create a new group named `devops`.
3. Add `alice` to the `devops` group.
4. Display `alice`'s user and group information.
5. Delete the user `alice` and remove their home directory.

---

## 3: File Permissions

### Tasks:

1. Create a new file called `testfile`.
2. Set `testfile`'s permissions to `755` using numeric mode.
3. Change the file's user permission to remove execute access using symbolic mode.
4. Change the file owner to your current user.
5. Set SUID, SGID, and sticky bits on `testfile`.

---

## 4: Sudo and System Files

### Tasks:

1. Create a new user `bob`.
2. Add `bob` to the `sudo` group.
3. Use `sudo` to run a command as another user.
4. View the contents of `/etc/passwd`, `/etc/group`, and `/etc/shadow`.

---

## 5: Command Line I/O and Piping

**Objective**: Practice using redirection and pipes.

### Tasks:

1. Redirect a command's output to a file.
2. Redirect error output to a separate file.
3. Pipe the output of `ls -la` into `grep` to filter results.
4. Chain commands using multiple pipes.
5. Use `tee` to write output to a file and display it on the terminal.

---

##  6: Text Processing Tools

**Objective**: Use tools like `cut`, `wc`, `grep`, `sort`, and `uniq`.

### Tasks:

1. Use `cut` to extract the usernames from `/etc/passwd`.
2. Use `wc` to count the number of lines in `/etc/passwd`.
3. Use `grep` to find all lines in `/etc/passwd` containing `/bin/bash`.
4. Sort and remove duplicate usernames in `/etc/passwd`.
5. Create a command chain that shows the most frequent commands from your history.

---

## Bonus: Integrated Challenge 

### Scenario:

You are setting up a system with the following requirements:
- A user `devuser` must be created and added to a group `devgroup`.
- A file `/tmp/devfile.txt` must be created with custom content.
- The file should have specific permissions and ownership.
- Use text processing tools to extract, filter, and analyze the file’s contents.

### Tasks:

1. Create the user `devuser` and group `devgroup`.
2. Add `devuser` to `devgroup`.
3. Create the file `/tmp/devfile.txt` with at least two lines (e.g., containing “error” and “info” messages).
4. Change the file’s ownership to `devuser:devgroup` and set permissions to `640`.
5. Use `grep`, `cut`, and `tee` to extract and log error messages from the file.
