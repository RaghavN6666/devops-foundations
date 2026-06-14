# Day 2 - Linux Permissions & Ownership

## Date

2025-06-15

## Time Studied

~1.5 Hours

---

# Objectives

- Understand Linux file permissions
- Learn how ownership works
- Understand users and groups
- Learn permission modification using chmod
- Learn ownership modification using chown
- Understand the purpose of umask
- Practice reading Linux permission strings

---

# Resources Used

## Linux Journey

Completed:

- File Permissions
- Modifying Permissions
- Ownership Permissions
- Umask

---

# Technical Notes

## Why Permissions Exist

Linux is a multi-user operating system.

Permissions exist to:

- Protect files from unauthorized access
- Prevent accidental modifications
- Separate responsibilities between users
- Improve system security

Without permissions, any user could modify or delete important system files.

---

# Permission Structure

Example:

```text
-rw-r--r--
```

Linux permissions are divided into:

```text
Owner | Group | Others
```

Example:

```text
-rw- r-- r--
```

### Breakdown

| Section | Meaning |
|----------|----------|
| Owner | Read + Write |
| Group | Read Only |
| Others | Read Only |

---

## First Character Meaning

The first character indicates the file type.

### Examples

```text
-  = Regular File
d  = Directory
l  = Symbolic Link
```

Example:

```text
-rw-r--r--
```

Regular file.

Example:

```text
drwxr-xr-x
```

Directory.

---

# Permission Symbols

## Read (r)

For files:

```text
Allows viewing file contents.
```

---

## Write (w)

For files:

```text
Allows modifying file contents.
```

---

## Execute (x)

For files:

```text
Allows execution of the file as a program or script.
```

---

# Directory Permissions

Directory permissions behave differently from file permissions.

---

## Read (r)

Allows listing directory contents.

Example:

```bash
ls directory/
```

---

## Write (w)

Allows:

- Creating files
- Deleting files
- Renaming files

inside the directory.

---

## Execute (x)

Allows entering or traversing the directory.

Example:

```bash
cd directory/
```

requires execute permission.

### Important Note

For directories:

```text
x ≠ executable file
```

Instead:

```text
x = permission to enter the directory
```

---

# Reading Permission Strings

Example:

```text
drwxr-xr-x
```

### Breakdown

```text
d
```

Directory

```text
rwx
```

Owner:
- Read
- Write
- Execute

```text
r-x
```

Group:
- Read
- Execute

```text
r-x
```

Others:
- Read
- Execute

---

# chmod

## Purpose

Changes file or directory permissions.

### Examples

```bash
chmod 777 file.txt
```

```bash
chmod 644 notes.txt
```

```bash
chmod 755 script.sh
```

---

## Numeric Permissions

### 7

```text
rwx
```

### 6

```text
rw-
```

### 5

```text
r-x
```

### 4

```text
r--
```

### 0

```text
---
```

---

# Why chmod 777 Is Dangerous

Command:

```bash
chmod 777 file.txt
```

Meaning:

```text
Owner  -> rwx
Group  -> rwx
Others -> rwx
```

### Security Risk

Any user can:

- Read the file
- Modify the file
- Delete the file

On production systems this is usually considered poor security practice.

---

# chown

## Purpose

Changes ownership of files and directories.

### Example

```bash
sudo chown user:filegroup file.txt
```

### Difference From chmod

```text
chmod = Changes permissions

chown = Changes ownership
```

---

# Users and Groups

Linux permissions are built around:

```text
Owner
Group
Others
```

This structure allows administrators to grant different levels of access to different users.

### Example

A development team may share access through a group while restricting access from everyone else.

---

# Umask

## Purpose

Controls the default permissions assigned to newly created files and directories.

Instead of changing permissions manually every time, Linux applies a default permission set based on the current umask value.

### Benefit

Improves security and reduces manual configuration effort.

---

# Knowledge Assessment

## Successfully Understood

### Permission Strings

Able to interpret:

```text
-rw-r--r--
```

and

```text
drwxr-xr-x
```

correctly.

---

### chmod vs chown

Understood the distinction between:

- Changing permissions
- Changing ownership

---

### Security Implications

Understood why:

```bash
chmod 777
```

can be dangerous on shared systems.

---

# Commands Practiced

```bash
ls -l
chmod
chown
```

Reviewed:

```bash
pwd
cd
ls
cat
less
find
```

---

# Mistakes Made

## Mistake 1

Initially misunderstood the execute permission on directories.

### Incorrect Assumption

```text
Execute permission makes files executable.
```

### Correct Understanding

For directories:

```text
Execute permission allows entering/traversing the directory.
```

---

## Mistake 2

While revisiting Bandit Level 2 → 3, I remembered the objective but forgot how to handle filenames containing spaces.

### Reminder

Examples:

```bash
cat "file name with spaces"
```

or

```bash
cat file\ name\ with\ spaces
```

### Lesson Learned

Special characters and spaces in filenames require quoting or escaping.

---

# Questions Raised

1. How do symbolic links work?
2. How are permissions stored internally by Linux?
3. What are common real-world use cases for groups?
4. How does Linux determine file ownership when new files are created?
5. How do Docker containers handle permissions?

---

# Personal Reflection

Today's session felt more intuitive than Day 1 because the concepts were connected to real-world security and system administration.

The most interesting realization was that Linux permissions are not just random symbols. They provide a structured way to control access across multiple users and groups.

I particularly enjoyed learning how to interpret permission strings because what initially looked like a random sequence of characters now conveys meaningful information about access control.

One concept that required extra attention was directory execute permissions. My initial assumption was incorrect, but after reviewing the material I understood that execute permissions on directories control traversal rather than execution.

While revisiting Bandit, I also discovered that I had forgotten how to handle filenames containing spaces. Although I remembered the overall concept, this reminded me that practical usage requires consistent repetition.

Overall, I feel significantly more comfortable reading Linux permissions than I did before this session.

---

# Key Takeaways

- Learned how Linux permissions are structured.
- Understood Owner, Group, and Others.
- Learned the meaning of read, write, and execute permissions.
- Learned the difference between file permissions and directory permissions.
- Understood the purpose of chmod.
- Understood the purpose of chown.
- Learned why chmod 777 is often a security risk.
- Gained a basic understanding of umask.

---

# Self Assessment

| Skill | Rating |
|---------|---------|
| Linux Navigation | 5.5/10 |
| Linux Permissions | 6.5/10 |
| Git | 3.5/10 |
| Networking | 2/10 |
| Python | 3/10 |

---

# Next Focus Areas

- Linux Processes
- Process Monitoring
- ps
- top
- kill
- Signals
- Background and Foreground Jobs

---

# Day 2 Completion Status

## Completed

- [x] File Permissions
- [x] chmod
- [x] chown
- [x] Ownership Permissions
- [x] Umask
- [x] Linux Permissions Assessment

## Pending

- [ ] Linux Processes
- [ ] Signals
- [ ] Process Monitoring
- [ ] Background Jobs
- [ ] Bandit Refresher